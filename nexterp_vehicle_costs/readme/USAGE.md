# Usage

## Linking invoice lines to vehicle costs

### Recording a vehicle expense from a supplier invoice

1. Open or create a supplier invoice (*Accounting → Vendors → Bills*).
2. On each invoice line that relates to a vehicle, fill in the **Vehicle Service Type** field (`fleet_service_type_id`) to categorise the expense (e.g. fuel, maintenance, insurance).
3. If the product on the line has **Generate Vehicle Contract** enabled (`vehicle_contract = True`), a `fleet.vehicle.log.contract` record is created automatically on validation.
4. Validate the invoice. Vehicle cost logs appear linked to the relevant vehicle.
5. Use the smart buttons **Vehicle Services** and **Vehicle Contracts** that appear on the invoice form (`has_vehicle_services` / `has_vehicle_contracts`) to jump directly to the generated cost records.

### Cancelling an invoice with vehicle costs

1. Click **Reset to Draft** / **Cancel** on the invoice. The module's `button_cancel` override automatically reverses (`cancel_vehicle_cost`) the associated `fleet.vehicle.log.services` or `fleet.vehicle.log.contract` entries so the vehicle history stays accurate.

## Linking stock moves to vehicle costs

### Recording a refuelling from a warehouse receipt

1. Open a receipt or internal transfer (*Inventory → Operations → Transfers*).
2. On the detailed move form, set the **Vehicle** field (`vehicle_id`) on the stock move line.
3. Tick **Refuel** (`refuel = True`) if the move represents a fuel top-up.
4. The **Vehicle Service Type** (`fleet_service_type_id`) is computed automatically from the product; you can override it on the move form.
5. Validate the transfer. The module's `_action_done` hook calls `create_vehicle_cost`, writing a `fleet.vehicle.log.services` record linked via `move_line_id` and `stock_move_id`.

## Fleet reporting

### Costs Analysis Log

1. Go to **Fleet → Reporting → Costs Log**.
2. Use the search bar to filter by vehicle, service type, date range, or owner.
3. Switch between the **list** and **pivot** views to analyse total expenditure per vehicle or category.

![Costs Analysis Log pivot view](./fleet_costs_log_pivot.png)
