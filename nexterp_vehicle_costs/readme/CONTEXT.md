# Key features

- **Vehicle costs from supplier invoices** — each invoice line can be tagged with a `fleet_service_type_id`; validating the bill creates `fleet.vehicle.log.services` or `fleet.vehicle.log.contract` records automatically.
- **Vehicle costs from stock moves** — warehouse receipts and transfers can be linked to a vehicle and optionally flagged as a refuel, generating service log entries on transfer validation.
- **Automatic cost reversal** — cancelling an invoice or stock transfer cancels the associated vehicle cost logs, keeping the fleet history consistent.
- **Contract generation from products** — enabling `vehicle_contract` on a product template triggers automatic contract log creation whenever that product appears on a supplier bill.
- **Romanian non-deductible VAT support** — per-vehicle `not_deductible` flag and `l10n_ro_nondeductible_percent` integrate with the `l10n_ro_nondeductible_vat` localization module.
- **Vehicle ownership tracking** — `owner_id` on the vehicle propagates to all service and contract logs for partner-level cost analysis.
- **Costs Analysis Log report** — dedicated pivot and list report under *Fleet → Reporting → Costs Log* with filtering by vehicle, service type, and date.
- **Pre-loaded fuel service type** — ships with a *Realimentare* service type ready for Romanian fuel cost tracking.
