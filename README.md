import pandas as pd
import numpy as np
from datetime import datetime, timedelta
import random
import os

random.seed(42)
np.random.seed(42)

OUTPUT_DIR = "sample_data"
os.makedirs(OUTPUT_DIR, exist_ok=True)

# ── Customers ──────────────────────────────────────────
cities = ["Mumbai", "Delhi", "Bangalore", "Chennai", "Hyderabad", "Pune"]
customers = pd.DataFrame({
    "customer_id": [f"C{str(i).zfill(4)}" for i in range(1, 501)],
    "name": [f"Customer_{i}" for i in range(1, 501)],
    "email": [f"user{i}@example.com" for i in range(1, 501)],
    "city": [random.choice(cities) for _ in range(500)],
    "signup_date": [
        (datetime(2023, 1, 1) + timedelta(days=random.randint(0, 365))).strftime("%Y-%m-%d")
        for _ in range(500)
    ]
})
customers.to_csv(f"{OUTPUT_DIR}/customers.csv", index=False)
print(f"✅ customers.csv — {len(customers)} rows")

# ── Products ───────────────────────────────────────────
categories = ["Electronics", "Clothing", "Books", "Home", "Sports"]
products = pd.DataFrame({
    "product_id": [f"P{str(i).zfill(4)}" for i in range(1, 101)],
    "name": [f"Product_{i}" for i in range(1, 101)],
    "category": [random.choice(categories) for _ in range(100)],
    "price": [round(random.uniform(99, 9999), 2) for _ in range(100)],
    "stock_qty": [random.randint(0, 500) for _ in range(100)]
})
products.to_csv(f"{OUTPUT_DIR}/products.csv", index=False)
print(f"✅ products.csv — {len(products)} rows")

# ── Orders ─────────────────────────────────────────────
statuses = ["completed", "cancelled", "returned", "processing"]
orders = pd.DataFrame({
    "order_id": [f"O{str(i).zfill(6)}" for i in range(1, 5001)],
    "customer_id": [f"C{str(random.randint(1,500)).zfill(4)}" for _ in range(5000)],
    "product_id": [f"P{str(random.randint(1,100)).zfill(4)}" for _ in range(5000)],
    "quantity": [random.randint(1, 5) for _ in range(5000)],
    "amount": [round(random.uniform(99, 49999), 2) for _ in range(5000)],
    "status": [random.choice(statuses) for _ in range(5000)],
    "created_at": [
        (datetime(2024, 1, 1) + timedelta(days=random.randint(0, 364))).strftime("%Y-%m-%d %H:%M:%S")
        for _ in range(5000)
    ]
})
orders.to_csv(f"{OUTPUT_DIR}/orders.csv", index=False)
print(f"✅ orders.csv — {len(orders)} rows")

# ── Inventory ──────────────────────────────────────────
warehouses = ["WH-NORTH", "WH-SOUTH", "WH-EAST", "WH-WEST"]
inventory = pd.DataFrame({
    "product_id": [f"P{str(i).zfill(4)}" for i in range(1, 101)],
    "warehouse_id": [random.choice(warehouses) for _ in range(100)],
    "qty_on_hand": [random.randint(0, 1000) for _ in range(100)],
    "updated_at": [
        (datetime(2024, 6, 1) + timedelta(hours=random.randint(0, 720))).strftime("%Y-%m-%d %H:%M:%S")
        for _ in range(100)
    ]
})
inventory.to_csv(f"{OUTPUT_DIR}/inventory.csv", index=False)
print(f"✅ inventory.csv — {len(inventory)} rows")

print("\n🎉 All sample data generated in ./sample_data/")