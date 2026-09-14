# ✈️ Vueling GNB Transactions API (`vueling-netcore-api`)

> Enterprise currency exchange & transaction settlement REST API built with **ASP.NET Core**, **Entity Framework Core (SQLite)**, and **AutoMapper**. Developed as a technical challenge for Vueling.

---

## 💼 Business Domain & Challenge (GNB)

Goliath National Bank (GNB) operates international transactions across multiple international currencies. This service ingests:
1. **Exchange Rates** — Directed conversion rates between currency pairs (e.g. `USD -> CAD`, `CAD -> EUR`), requiring graph pathfinding when direct exchange rates do not exist.
2. **Transactions** — High-volume transaction lists with SKUs, amounts, and source currencies.
3. **SKU Aggregation** — Computes the total consolidated revenue per SKU converted accurately into **EUR** using bankers' rounding and rate chain resolution.

---

## 🏛️ Architecture & Clean Code Patterns

- **Repository & Service Pattern** — Complete decoupling between controller endpoints, exchange rate calculation engine, and persistence queries.
- **SQLite Database** — Embedded relational database via Entity Framework Core (`Microsoft.EntityFrameworkCore.Sqlite`) for portable, deterministic local execution.
- **DTO Transformation Layer** — Strict separation between internal database entities and public API contracts mapped via **AutoMapper**.
- **Currency Graph Solver** — Resolves indirect multi-hop currency conversions where direct currency pairs are absent.

---

## 📡 API Endpoints

Base route: `/api/gnb`

| Method | Route | Description |
| :--- | :--- | :--- |
| `GET` | `/api/gnb/rates` | Retrieve all current currency exchange rates |
| `GET` | `/api/gnb/transactions` | Retrieve all recorded international transactions |
| `GET` | `/api/gnb/transactions/{sku}` | Retrieve all transactions for a specific SKU and compute total sum in **EUR** |

---

## 🛠️ Tech Stack

- **Framework**: ASP.NET Core 2.2 Web API
- **Language**: C#
- **Database**: SQLite / EF Core Sqlite
- **Mapping**: AutoMapper
- **Pattern**: Repository Pattern, Dependency Injection, DTOs

---

## 🚀 Running Locally

### Prerequisites
- [.NET Core SDK](https://dotnet.microsoft.com/download)

### Build & Run

```bash
# Clone the repository
git clone https://github.com/oscar-lopez-dev/vueling-netcore-api.git
cd vueling-netcore-api

# Restore packages
dotnet restore

# Run the API
dotnet run --project GNB.AspNetCore.Application
```

The service will start and serve requests at `http://localhost:5000` (or `https://localhost:5001`).

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
