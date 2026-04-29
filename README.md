# 🧺 Mini Laundry Order Management System

> Assignment | Python | Jupyter Notebook | In-memory storage

---

## 🚀 Setup Instructions

### Prerequisites
- Python 3.9+
- Jupyter Notebook or JupyterLab

### Install & Run

```bash
# 1. Clone the repo
git clone https://github.com/YOUR_USERNAME/laundry-oms.git
cd laundry-oms

# 2. Install dependencies
pip install tabulate jupyter

# 3. Launch notebook
jupyter notebook laundry_oms.ipynb
```

### How to Run
- Run cells **top to bottom** (Cell 1 → Cell 10)
- Cells 1–4 are setup (config, DB, logic, display)
- Cells 5–9 are auto-demo (creates orders, updates status, filters, dashboard, validation tests)
- Cell 10 is the **interactive CLI** — uncomment `interactive_menu()` and run to use it manually

---

## ✅ Features Implemented

| Feature | Status |
|---------|--------|
| Create order with customer name, phone, garments, qty | ✅ |
| Auto price calculation from price catalogue | ✅ |
| Unique Order ID generation (e.g. `ORD-A1B2C3D4`) | ✅ |
| Total bill output on order creation | ✅ |
| Status workflow: RECEIVED → PROCESSING → READY → DELIVERED | ✅ |
| Forward-only status transitions | ✅ |
| Status history audit trail with timestamps | ✅ |
| Estimated ready date (+2 days from creation) | ✅ |
| List all orders | ✅ |
| Filter by status | ✅ |
| Filter by customer name (partial, case-insensitive) | ✅ |
| Filter by phone number | ✅ |
| Filter by garment type | ✅ |
| Dashboard: total orders, revenue, orders per status | ✅ |
| Dashboard: top garments by quantity | ✅ |
| Input validation (phone, garment, qty, name) | ✅ |
| Interactive CLI inside notebook | ✅ |

---

## 🤖 AI Usage Report

### Tool Used
**Claude (Anthropic)** — used occasionally when I got stuck on specific problems.

I built the overall structure, logic, and flow myself. Claude helped me unblock a few specific things:

---

### Where I Used Claude & Why

**1. Generating unique Order IDs**

I wasn't sure of the cleanest way to generate short readable IDs like `ORD-A1B2C3D4`. I asked Claude:
> "What's a good way to generate short unique order IDs in Python?"

It suggested using `uuid4()` and slicing the first 8 characters. I adapted that into my own format.

**2. Forward-only status transition logic**

I knew I wanted to prevent backward transitions but wasn't sure how to enforce it cleanly without a long if-else chain. I asked:
> "How do I enforce ordered state transitions in Python without a big if-else block?"

Claude suggested using `list.index()` to compare positions. I wrote the actual implementation and added the edge case check for same-status updates myself.

**3. Tabulate formatting**

I had never used the `tabulate` library before. I asked:
> "How do I use tabulate to print a table with custom headers in Python?"

Used the docs example Claude gave as a reference, then built my own display functions around it.

**4. Status history audit trail**

I wanted to log every status change with a timestamp but wasn't sure of the right data structure. Asked:
> "What's a simple way to maintain a history log of state changes in a Python dict?"

Claude suggested a list of `{status, changed_at}` dicts appended on each update. Simple and clean — I implemented it directly.

---

### What I Fixed / Improved Myself

- Claude's `tabulate` example didn't include the `estimated_ready` column — I added that myself
- The interactive CLI input wasn't normalising case, so `shirt` would fail the catalogue lookup — I added `.strip().title()` to fix it
- Added the empty-garments guard in the interactive CLI loop myself after testing showed it crashed on `done` with no items entered

---

## ⚖️ Tradeoffs

### What I Skipped
- **Persistent storage** — data resets on kernel restart; would use SQLite with more time
- **REST API** — kept it as pure functions; would wrap in FastAPI given more time
- **Authentication** — out of scope for this version
- **Frontend** — the notebook is the interface

### What I'd Improve With More Time
- SQLite backend so data survives kernel restarts
- FastAPI wrapper + Postman collection
- `ipywidgets` for a proper in-notebook GUI
- Unit tests with `pytest`
- Deploy on Railway or Render

##📷 **Screenshots**
<img width="1431" height="1069" alt="Screenshot 2026-04-29 212959" src="https://github.com/user-attachments/assets/1d3566b9-003d-4f14-91d5-60f615cd30ed" />
<img width="1208" height="539" alt="Screenshot 2026-04-29 213011" src="https://github.com/user-attachments/assets/77113b2b-1616-43cd-8b4f-caad75a65b5c" />
<img width="1249" height="383" alt="Screenshot 2026-04-29 213054" src="https://github.com/user-attachments/assets/8a13f827-8be5-458e-a07b-c682aeed588d" />
<img width="1283" height="565" alt="Screenshot 2026-04-29 213109" src="https://github.com/user-attachments/assets/6e195de2-4164-4c75-9b23-bc5fa8274540" />
<img width="823" height="469" alt="Screenshot 2026-04-29 213147" src="https://github.com/user-attachments/assets/36621160-3bb9-4ba1-8efb-07a64b3ace31" />



