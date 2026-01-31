# Modular Monolith Skeleton (.NET 10)

This repository contains a production-ready modular monolith skeleton with strict layering, EF Core code-first, and module boundaries.

## Solution Structure

```
src/
  App.Host/
  BuildingBlocks/
  Modules/
    Identity/
      Identity.Api/
      Identity.Application/
      Identity.Domain/
      Identity.Infrastructure/
    Sales/
      Sales.Api/
      Sales.Application/
      Sales.Domain/
      Sales.Infrastructure/
    Inventory/
      Inventory.Api/
      Inventory.Application/
      Inventory.Domain/
      Inventory.Infrastructure/
```

## EF Core Migrations

All modules use the same SQL Server database, each with its own schema and migrations in the Infrastructure project.

### Identity

```
dotnet ef migrations add Initial --project src/Modules/Identity/Identity.Infrastructure --startup-project src/App.Host --context Identity.Infrastructure.IdentityDbContext
dotnet ef database update --project src/Modules/Identity/Identity.Infrastructure --startup-project src/App.Host --context Identity.Infrastructure.IdentityDbContext
```

### Sales

```
dotnet ef migrations add Initial --project src/Modules/Sales/Sales.Infrastructure --startup-project src/App.Host --context Sales.Infrastructure.SalesDbContext
dotnet ef database update --project src/Modules/Sales/Sales.Infrastructure --startup-project src/App.Host --context Sales.Infrastructure.SalesDbContext
```

### Inventory

```
dotnet ef migrations add Initial --project src/Modules/Inventory/Inventory.Infrastructure --startup-project src/App.Host --context Inventory.Infrastructure.InventoryDbContext
dotnet ef database update --project src/Modules/Inventory/Inventory.Infrastructure --startup-project src/App.Host --context Inventory.Infrastructure.InventoryDbContext
```
