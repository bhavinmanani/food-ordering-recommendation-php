# Project Workflow

How the system behaves from the user's point of view. Everything below was traced from the source code: the file names in brackets are the pages that do the work.

---

## 1. Customer journey

```mermaid
flowchart TD
    A[Open home page<br/>index.php] --> B{Logged in?}
    B -- No --> C[Register<br/>registration.php]
    C --> D[Login<br/>login.php]
    B -- No --> D
    D -->|username + password match| E[Session user_id set]
    B -- Yes --> E
    E --> F[Browse restaurants<br/>restaurants.php / index.php]
    F --> G[Pick a restaurant<br/>dishes.php?res_id=...]
    G --> H[Add dish + quantity to cart<br/>product-action.php]
    H --> I{Add more or checkout?}
    I -- Add more --> G
    I -- Checkout --> J[Order summary<br/>checkout.php]
    J --> K[Choose Cash on Delivery<br/>and confirm the order]
    K --> L[One row per cart item<br/>saved in users_orders]
    L --> M[Track or cancel order<br/>your_orders.php]
```

**Notes**
- The cart lives in the PHP session (`$_SESSION["cart_item"]`), so it is lost on logout or when the session ends.
- Adding the same dish twice increases its quantity instead of creating a second line.
- `checkout.php` redirects to `login.php` if there is no logged-in customer.
- Payment options: **Cash on delivery** works; **PayPal** is displayed but disabled.

---

## 2. Cart actions

`dishes.php` includes `product-action.php`, which reads `?action=` from the URL.

| `action` | What it does |
|---|---|
| `add` | Looks up the dish by id (prepared statement) and adds it, or increases quantity if already in the cart |
| `remove` | Removes one dish from the cart |
| `empty` | Clears the whole cart |
| `check` | Redirects to `checkout.php` |

---

## 3. Order status lifecycle

The admin changes the status in `admin/order_update.php`. The customer sees it in `your_orders.php`.

```mermaid
stateDiagram-v2
    [*] --> New: Customer places order<br/>(status empty, shown as "Dispatch")
    New --> InProcess: Admin sets "in process"<br/>(shown as "On a Way!")
    InProcess --> Closed: Admin sets "closed"<br/>(shown as "Delivered")
    New --> Rejected: Admin sets "rejected"<br/>(shown as "Cancelled")
    InProcess --> Rejected: Admin sets "rejected"
    New --> Deleted: Customer cancels<br/>(row is deleted)
    Closed --> [*]
    Rejected --> [*]
    Deleted --> [*]
```

Each admin status change also writes a row to the `remark` table (order id, status, remark text, date), so there is a small history of what the admin wrote.

**Important:** the code does not force this order. The admin can pick any of the three statuses at any time, and "cancel" by the customer is a hard delete, not a status.

---

## 4. Admin workflow

```mermaid
flowchart TD
    A[Admin login<br/>admin/index.php] -->|match in admin table| B[Dashboard<br/>admin/dashboard.php]
    B --> C[Users<br/>allusers / add_users / update_users]
    B --> D[Store<br/>allrestraunt / add_restraunt / update_restraunt<br/>update_category]
    B --> E[Menu<br/>all_menu / update_menu]
    B --> F[Orders<br/>all_orders]
    F --> G[view_order.php<br/>see one order]
    G --> H[order_update.php<br/>set status + write remark]
```

Dashboard tiles show the total number of restaurants, dishes, users and orders (simple `SELECT *` row counts).

Admin registration exists on the admin login page. A new admin must enter a **one-time registration code** that exists in the `admin_codes` table; once used, the code is stored on the new admin row and is rejected as "already redeemed" next time.

---

## 5. Request → page → table map

| Action | Page | Tables touched |
|---|---|---|
| Register | `registration.php` | `users` (read to check duplicates, then insert) |
| Login | `login.php` | `users` |
| List restaurants / categories | `index.php`, `restaurants.php` | `restaurant`, `res_category` |
| View a menu | `dishes.php` | `restaurant`, `dishes` |
| Place order | `checkout.php` | `users_orders` (insert) |
| View my orders | `your_orders.php` | `users_orders` |
| Cancel an order | `delete_orders.php` | `users_orders` (delete) |
| Admin login | `admin/index.php` | `admin` |
| Update order status | `admin/order_update.php` | `remark` (insert), `users_orders` (update) |
| Manage users / restaurants / dishes | `admin/*.php` | `users`, `restaurant`, `dishes`, `res_category` |

---

## 6. Development workflow I would use if rebuilding this

1. Requirements and user stories (customer, admin)
2. Database design (ER diagram → tables)
3. Static pages with Bootstrap
4. PHP logic for register/login, then menu, cart, checkout, orders
5. Admin panel
6. Manual testing with the checklist in [PROJECT_DOCUMENTATION.md](PROJECT_DOCUMENTATION.md#7-testing)
7. Security pass (prepared statements, password hashing, access checks)
