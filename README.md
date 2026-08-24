# TPLS Professional Multi-Role Portals — Updated

The Progress of Life School

## Included
- Advanced Admin Portal
- Advanced Teacher Portal
- Multi-role teaching staff model
- Teacher + Financial Secretary / Accountant access in the same login
- High Section / Low Section Coordinator responsibilities remain additive to teaching access
- Forgot-password flow
- Student and teacher photo storage through Supabase Storage
- On-demand browser reports/print views
- Principal photograph and Principal's Message on both portals

## Supabase
The portals use the existing project reference `znjtsykmpuhprikbscut` and the publishable key already configured in the portal files.

Run `TPLS_ADVANCED_PORTAL_COMPLETE_SUPABASE_SETUP.sql` in the existing project before deployment if you have not already done so.

## Important: PGRST303 / JWT issued at future
If Supabase Auth accepts sign-in but the Data API returns:
`PGRST303: JWT issued at future`
this is a JWT time-validation problem, not a missing school table. The current portal includes a retry and a clearer diagnostic message. If it persists on a correctly synchronized computer, wait and retry; if it continues, contact Supabase support with project ref `znjtsykmpuhprikbscut`, because the issue may be clock synchronization between Supabase Auth and the Data API.

## Deployment
Upload the contents of `Admin Portal` and `Teacher Portal` to their respective static hosts. Keep the folder structure inside each portal intact.


## FULL FUNCTIONAL FINANCIAL SECRETARY UPDATE
This version makes the Financial Secretary + Teacher role operational in the same login.
- Collect fees for any active student.
- Record discounts and payment dates.
- Generate a TPLS fee receipt PDF on demand.
- Add school expenses to the shared cloud ledger.
- Review live fee/expense records and download the financial report.
- Teaching features remain active for the same account.

### Required Supabase step
Run `TPLS_FINANCIAL_SECRETARY_FUNCTIONAL_SETUP.sql` once in the existing Supabase project. This migration replaces policies on `fee_payments` and `expenses` with recursion-safe role-aware policies: Admin has full control, ordinary teachers can view only payments for their assigned students, Financial Secretary can collect fees/add or correct expenses, and Accountant can review the financial ledger.

Do not use a service-role key in the browser. The portal continues to use the existing publishable Supabase key.
