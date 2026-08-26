# Configuration

## 1. Mark products that generate vehicle contracts

1. Go to **Inventory → Products → Products** (or **Purchase → Products → Products**).
2. Open the product used on supplier invoices for recurring vehicle costs (e.g. insurance, leasing).
3. On the **General Information** tab, enable **Generate Vehicle Contract** (`vehicle_contract`).
4. From now on, posting a supplier invoice line with this product automatically creates a `fleet.vehicle.log.contract` entry.

## 2. Configure vehicle non-deductible VAT (Romania)

This module depends on `l10n_ro_nondeductible_vat`. For each vehicle where VAT is partially or fully non-deductible:

1. Open the vehicle record (*Fleet → Fleet → Vehicles*).
2. Set **Non Deductible** (`not_deductible`) and choose the **Romania – Non Deductible Percent** (`l10n_ro_nondeductible_percent`).
3. Assign the appropriate **Non-Deductible Tax** (`tax_non_deductible`) — the tax that will be applied to invoice lines associated with this vehicle.

## 3. Set vehicle ownership

1. On the vehicle form (*Fleet → Fleet → Vehicles*), set the **Owner** field (`owner_id`) to the partner who owns the vehicle.
2. This value is automatically propagated (`related`) to service logs (`fleet.vehicle.log.services`) and contract logs (`fleet.vehicle.log.contract`) for filtering in reports.

## 4. Review fleet service type categories

1. Go to **Fleet → Configuration → Service Types**.
2. Ensure each service type has the correct **Category** value (e.g. `fuel`, `contract`, `service`) set in the `category` selection field — this drives the separation between *services* and *contracts* on invoices.
3. The module ships a pre-loaded service type **Realimentare** (`data_fleet_service_type_refuel`) for fuel top-ups.
