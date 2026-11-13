VentureBill — Final Product Architecture & Development Blueprint  
(Architecture finalized) (Hybrid product)

Your decisions are finalized:  
Decision	Final selection  
Product name	VentureBill  
Product type	Hybrid Desktop \+ Cloud  
Target customers	General businesses across India  
Source reuse	Full reuse of useful original functionality  
Original billing	Retain  
GST functionality	Retain and modernize  
Desktop platform	Windows-first, expandable to macOS/Linux  
Offline operation	Mandatory for core billing  
Commercial distribution	Your own independent product  
Database	PostgreSQL \+ local SQLite  
Frontend	React \+ TypeScript  
Backend	Node.js \+ TypeScript  
Desktop framework	Electron

1\. Product vision  
VentureBill will be a commercial business management and GST billing platform for Indian businesses.

It will combine the existing billing functionality with a modern multi-company, multi-user, hybrid architecture.

Product positioning  
VentureBill — Complete Business Billing, GST, Inventory and Financial Management.

The product should serve:  
\- Retail shops.  
\- Wholesalers.  
\- Distributors.  
\- Trading companies.  
\- Manufacturers.  
\- Service providers.  
\- Freelancers.  
\- Small and medium enterprises.  
\- Multi-branch businesses.  
Core product principles  
1\. Billing must work without internet.  
2\. GST calculations must be accurate and testable.  
3\. Business records must be protected.  
4\. Different businesses must never access one another's information.  
5\. Desktop and cloud records must synchronize safely.  
6\. Users must be able to control employee permissions.  
7\. Reports must be traceable to their source transactions.  
8\. Customers must be able to export and back up their data.  
9\. Updates must be controlled by VentureBill, not the original project.  
10\. Existing useful business features must not disappear during migration.  
2\. Important source-code audit finding  
There is one correction to the earlier preliminary analysis that changes how we should execute the project.

The ZIP listing currently shows:  
\- \_system/server.js  
\- \_system/src/utils.js  
\- \_system/src/utils/  
\- \_system/package.json  
\- \_system/package-lock.json  
\- \_system/README.md  
\- \_system/CHANGELOG.md  
\- \_system/node\_modules/  
However, the archive's dist/ directory is empty in the ZIP listing, and the original React frontend source tree is not present.

This means we must not assume that the uploaded ZIP is a complete development repository.

(Source recovery required)

Before modifying VentureBill  
1\. Recover the complete original React source.  
2\. Identify the exact source revision corresponding to the uploaded release.  
3\. Compare its backend and dependencies with the ZIP.  
4\. Run the original application.  
5\. Record baseline functionality and calculations.  
6\. Create a separate VentureBill repository.  
Original project reference:

Original Free GST Billing source repository

Do not develop against a random newer branch without checking compatibility. The ZIP contains a dated release snapshot, and the source revision must be matched to it.  
3\. Exact file-by-file modification plan  
This is the most important section for implementation.

We will maintain two repositories conceptually:  
\- Original reference: the Free GST Billing source, preserved for comparison and migration.  
\- New product: VentureBill, with independent branding, backend, database, frontend and release infrastructure.  
Never modify the only copy of the original.  
3.1 Existing files: keep, modify, replace or remove  
The following paths are verified against the uploaded archive. Some files are retained as migration references, rather than copied unchanged into the new application.  
Root-level files  
Original file	Action	VentureBill change  
Free GST Billing \- WINDOWS.hta	Replace	New VentureBill installer/launcher  
Free GST Billing \- MAC.command	Replace	VentureBill macOS launcher  
Free GST Billing \- LINUX.sh	Replace	VentureBill Linux launcher  
READ ME FIRST.txt	Rewrite	VentureBill installation instructions

\_system/ files  
Existing file	Action	Reason  
server.js	Rewrite	Replace local JSON API with modular backend  
package.json	Rewrite	New dependencies, scripts and workspace  
package-lock.json	Regenerate	Match new dependency graph  
LICENSE	Keep obligations	Preserve original MIT notice and add VentureBill's own licensing terms  
README.md	Rewrite	New product documentation  
CHANGELOG.md	Replace	VentureBill release history  
dist/	Regenerate	New production frontend build  
node\_modules/	Remove from source control/release source	Install dependencies from lockfile  
data/	Replace	Local SQLite and migration/backup storage  
src/utils.js	Refactor	Separate business logic into packages  
src/utils/appHome.js	Adapt	Determine local application data directories  
src/utils/cashBook.js	Retain logic, rewrite persistence	Cash book service  
src/utils/errorReport.js	Adapt	VentureBill diagnostics  
src/utils/makeDir.js	Adapt	Storage initialization  
src/utils/purchaseOrders.js	Retain logic, rewrite persistence	Purchase-order service  
src/utils/purchasePayments.js	Retain logic, rewrite persistence	Supplier payment service  
src/utils/serverLock.js	Replace	Electron process lock and database locking  
src/utils/setupDownload.js	Replace	VentureBill update/download service  
scripts/bundle-tesseract-assets.mjs	Retain and adapt	Bundle OCR assets  
backup-windows.ps1	Rewrite	VentureBill backup system  
restore-windows.ps1	Rewrite	Verified restore process  
update-windows.ps1	Rewrite	Signed VentureBill updates  
install-windows.ps1	Rewrite	VentureBill installation  
install-unix.sh	Rewrite	Unix installation  
start-windows.ps1	Rewrite	Electron/server startup  
start-unix.sh	Rewrite	Desktop startup  
stop-windows.ps1	Rewrite	Graceful shutdown  
open-app.sh	Rewrite	VentureBill desktop startup  
uninstall-windows.ps1	Rewrite	Safe uninstall with data retention  
uninstall-unix.sh	Rewrite	Safe Unix uninstall  
update-unix.sh	Rewrite	Signed update workflow  
check-node.sh	Replace	Desktop runtime check  
ensure-node.ps1	Replace	Runtime management

Files to remove from the distributed source tree  
(Remove from production packaging)

These should not be shipped as loose internal development files:  
\_system/node\_modules/  
\_system/dist/                 \# old build only; regenerate  
original development installers  
original project promotional assets  
original project updater scripts  
original project branding  
original project support references  
original project donation information  
original development test artifacts

Do not remove the original LICENSE or the required MIT copyright notice.

Do not delete old business functionality just because it is not part of the first release.  
3.2 Frontend files: recovery and migration  
The uploaded ZIP does not contain the original frontend source components.

Consequently, the following is a proposed destination structure, not a claim that these files exist in your ZIP.

Once the matching original source is recovered, map the original components into this structure.  
Original functionality	New VentureBill destination  
Dashboard	apps/web/src/features/dashboard/  
Invoice editor	apps/web/src/features/sales/invoices/  
Invoice PDF	packages/pdf-engine/  
Clients	apps/web/src/features/customers/  
Products	apps/web/src/features/products/  
Inventory	apps/web/src/features/inventory/  
Purchase bills	apps/web/src/features/purchases/  
Purchase orders	apps/web/src/features/purchase-orders/  
Manufacturing	apps/web/src/features/manufacturing/  
Expenses	apps/web/src/features/expenses/  
Receipts	apps/web/src/features/payments/  
Cash book	apps/web/src/features/finance/cash-book/  
Recurring invoices	apps/web/src/features/automation/recurring/  
GST returns	apps/web/src/features/gst/returns/  
GSTR-2B reconciliation	apps/web/src/features/gst/reconciliation/  
Income tax	apps/web/src/features/tax/income-tax/  
Reports	apps/web/src/features/reports/  
Settings	apps/web/src/features/settings/  
OCR	apps/web/src/features/ocr/  
Backup	apps/desktop/src/services/backup/  
Synchronization	packages/sync-engine/  
Local storage	apps/desktop/src/services/local-db/

Migration rule: Preserve the existing feature's business behavior first. Change the persistence and presentation layers separately. This makes it much easier to identify regressions.  
4\. Exact module removal list  
You selected full source reuse, so my recommendation is to remove obsolete product identity and infrastructure, not valuable billing functionality.  
4.1 Remove completely  
Original element	Why remove  
Free GST Billing product name	Replaced by VentureBill  
Original logo	Brand ownership  
Original app icon	Brand ownership  
Original splash screen	Brand ownership  
Original promotional slogans	New positioning  
Original donation information	New commercial model  
Original supporter section	Original product identity  
Original support email	Your support infrastructure  
Original issue-reporting link	Your issue tracker  
Original update URL	Your release service  
Original documentation links	Your documentation  
Original installer names	New distribution  
Original application metadata	New identity  
Original product analytics, if any are added in upstream versions	Privacy and ownership

4.2 Replace completely  
These are not simply removed. They are replaced by VentureBill equivalents.  
Existing module	Replacement  
Local JSON database	SQLite \+ PostgreSQL  
Single local Express server	Modular API \+ local desktop service  
Local-only data ownership	Tenant/company data model  
PIN-only lock	Full account authentication and authorization  
GitHub updater	VentureBill release service  
Manual local backups	Local \+ encrypted cloud backups  
Local preferences	User/device preferences  
Original error logs	Centralized, privacy-conscious diagnostics  
Single-machine operation	Multi-device synchronization  
Original installer	Signed VentureBill installer  
Original local settings	Organization and user settings

4.3 Keep and modernize  
These are core intellectual and functional assets of the application.

(Preserve)

Billing engine  
\- Five original document types.  
\- GST tax splitting.  
\- Invoice numbering.  
\- Discount modes.  
\- Round-off.  
\- Credit balance.  
\- Invoice cancellation.  
\- PDF and thermal printing.  
\- Multi-currency.  
\- Custom terms.  
  Business management  
\- Customers.  
\- Products.  
\- Stock.  
\- Purchases.  
\- Purchase orders.  
\- Production.  
\- Expenses.  
\- Receipts.  
\- Cash book.  
\- Recurring billing.  
  Tax and reporting  
\- GSTR-1.  
\- GSTR-3B.  
\- GSTR-2B reconciliation.  
\- E-Way Bill exports.  
\- TDS/TCS.  
\- Income tax calculations.  
\- P\&L.  
\- COGS.  
\- Inventory valuation.  
Additional GST capabilities should be enabled according to applicable Indian law and verified tax rules, rather than being treated as universally applicable to every customer.  
5\. VentureBill technical architecture  
5.1 Hybrid architecture  
The hybrid model will have two environments.

Local desktop environment

Runs on the customer's Windows computer and continues operating without internet.

Cloud environment

Handles centralized business management, account management, synchronization, subscription administration, remote access and cloud backup.  
Architecture diagram  
                 VENTUREBILL CLIENTS  
                         \|  
          \+--------------+--------------+  
          \|              \|              \|  
       Desktop        Web App       Mobile Web  
       Electron        React          React  
          \|              \|              \|  
          \|              \+------+-------+  
          \|                     \|  
          v                     v  
   LOCAL APPLICATION       CLOUD API  
          \|                     \|  
   \+------+-------+       \+-----+------+  
   \|              \|       \|            \|  
 SQLite       Sync Queue  API Gateway  Auth Service  
   \|              \|       \|            \|  
   \+------+-------+       \+-----+------+  
          \|                     \|  
     Local Business        PostgreSQL  
       Operations               \|  
                               Redis  
                                \|  
                       Background Workers  
                                \|  
                       Object Storage  
                                \|  
                     External Integrations

Local desktop services  
Service	Responsibility  
Electron main process	Desktop lifecycle  
Renderer	React interface  
Local API	Local business operations  
SQLite	Local business database  
Sync worker	Synchronization  
Print service	Thermal and PDF printing  
Backup service	Local backup  
Update service	Signed updates  
Device identity	Register the desktop installation

Cloud services  
Service	Responsibility  
API	Business operations  
Authentication	Login and sessions  
Tenant service	Business isolation  
PostgreSQL	Central business data  
Redis	Caching and jobs  
Worker	Recurring tasks  
Object storage	PDF and document storage  
Notification service	Email/WhatsApp integrations  
Subscription service	Plan and entitlement management  
Admin service	Product administration

5.2 Offline synchronization strategy  
This is the most important technical component of VentureBill.

A common mistake is to create a desktop app with SQLite and later add a button called Sync.

That is not enough.

You need a proper synchronization protocol.  
Example: invoice created without internet  
1\. User creates invoice INV-001.  
2\. Electron sends request to local API.  
3\. Local API validates invoice.  
4\. SQLite saves invoice.  
5\. Invoice gets local transaction ID.  
6\. Sync event is added to outbox.  
7\. User can print the invoice.  
8\. Internet becomes available.  
9\. Sync worker sends pending event.  
10\. Cloud API validates event.  
11\. Cloud database saves invoice.  
12\. Server acknowledges event.  
13\. Local event is marked synchronized.

Required sync tables  
\- sync\_outbox  
\- sync\_inbox  
\- sync\_cursors  
\- device\_registrations  
\- sync\_conflicts  
\- sync\_runs  
Conflict rules  
Data	Conflict policy  
Invoice creation	Immutable creation event  
Invoice number	Server-reserved series or device-specific series  
Invoice item changes	Version-based optimistic concurrency  
Customer details	Version-based conflict review  
Product information	Version-based conflict review  
Stock movements	Append-only movements  
Payments	Append-only payment events  
Audit logs	Append-only  
User settings	Last-write-wins where safe  
GST configuration	Authorized admin changes with versioning

Important: Never use a simple last-write-wins rule for financial transactions.

For stock, use stock movement events, not just overwriting a stock quantity.

For invoices, once an invoice is issued, changes should happen through appropriate correction, cancellation or credit-note workflows, with audit history.  
5.3 Offline operation policy  
Operation	Offline support  
Login to previously authenticated desktop	Yes, controlled by offline session policy  
Create invoice	Yes  
Print invoice	Yes  
Customer management	Yes  
Product management	Yes  
Inventory movement	Yes  
Purchase entry	Yes  
Expense entry	Yes  
Cash book	Yes  
Payment receipt	Yes  
Local reports	Yes  
GST summary	Yes, using locally available data  
GSTR-2B download	No  
Cloud backup	No, queue for later  
Subscription renewal	No, with controlled grace period  
New user registration	No  
Cloud dashboard	No  
Cloud synchronization	No

A desktop user should not be locked out of an already authenticated local business simply because the internet is unavailable.  
6\. Complete VentureBill repository structure  
This is the target repository. It is deliberately modular so you can develop, test and deploy individual parts without breaking the rest of the product.  
VentureBill/  
│  
├── apps/  
│   │  
│   ├── web/  
│   │   ├── public/  
│   │   │   ├── logo.svg  
│   │   │   ├── favicon.svg  
│   │   │   └── manifest.webmanifest  
│   │   │  
│   │   └── src/  
│   │       ├── app/  
│   │       │   ├── App.tsx  
│   │       │   ├── router.tsx  
│   │       │   ├── providers/  
│   │       │   └── layouts/  
│   │       │  
│   │       ├── components/  
│   │       │   ├── ui/  
│   │       │   ├── forms/  
│   │       │   ├── tables/  
│   │       │   └── modals/  
│   │       │  
│   │       ├── features/  
│   │       │   ├── dashboard/  
│   │       │   ├── sales/  
│   │       │   ├── customers/  
│   │       │   ├── suppliers/  
│   │       │   ├── products/  
│   │       │   ├── inventory/  
│   │       │   ├── purchases/  
│   │       │   ├── manufacturing/  
│   │       │   ├── expenses/  
│   │       │   ├── payments/  
│   │       │   ├── cash-book/  
│   │       │   ├── recurring/  
│   │       │   ├── gst/  
│   │       │   ├── income-tax/  
│   │       │   ├── reports/  
│   │       │   ├── users/  
│   │       │   ├── branches/  
│   │       │   └── settings/  
│   │       │  
│   │       ├── hooks/  
│   │       ├── services/  
│   │       ├── store/  
│   │       ├── styles/  
│   │       └── main.tsx  
│   │  
│   ├── desktop/  
│   │   ├── electron/  
│   │   │   ├── main.ts  
│   │   │   ├── preload.ts  
│   │   │   ├── windows/  
│   │   │   ├── ipc/  
│   │   │   └── security/  
│   │   │  
│   │   ├── src/  
│   │   │   ├── local-api/  
│   │   │   ├── database/  
│   │   │   ├── printer/  
│   │   │   ├── backup/  
│   │   │   ├── sync/  
│   │   │   └── updates/  
│   │   │  
│   │   └── electron-builder.yml  
│   │  
│   └── admin/  
│       └── src/  
│           ├── dashboard/  
│           ├── tenants/  
│           ├── subscriptions/  
│           ├── plans/  
│           ├── support/  
│           ├── releases/  
│           └── audit/  
│  
├── services/  
│   ├── api/  
│   │   └── src/  
│   │       ├── modules/  
│   │       │   ├── auth/  
│   │       │   ├── tenants/  
│   │       │   ├── companies/  
│   │       │   ├── users/  
│   │       │   ├── customers/  
│   │       │   ├── suppliers/  
│   │       │   ├── sales/  
│   │       │   ├── inventory/  
│   │       │   ├── purchases/  
│   │       │   ├── finance/  
│   │       │   ├── gst/  
│   │       │   ├── reports/  
│   │       │   ├── sync/  
│   │       │   ├── subscriptions/  
│   │       │   └── audit/  
│   │       ├── middleware/  
│   │       ├── config/  
│   │       ├── database/  
│   │       ├── routes/  
│   │       └── server.ts  
│   │  
│   └── worker/  
│       └── src/  
│           ├── recurring/  
│           ├── notifications/  
│           ├── synchronization/  
│           ├── backups/  
│           └── reports/  
│  
├── packages/  
│   ├── gst-engine/  
│   ├── invoice-engine/  
│   ├── accounting-engine/  
│   ├── inventory-engine/  
│   ├── pdf-engine/  
│   ├── sync-engine/  
│   ├── shared-types/  
│   ├── validation/  
│   ├── ui/  
│   └── config/  
│  
├── database/  
│   ├── prisma/  
│   │   ├── schema.prisma  
│   │   ├── migrations/  
│   │   └── seed.ts  
│   ├── sqlite/  
│   │   ├── schema.sql  
│   │   └── migrations/  
│   └── scripts/  
│  
├── infrastructure/  
│   ├── docker/  
│   ├── nginx/  
│   ├── monitoring/  
│   ├── backup/  
│   └── deployment/  
│  
├── scripts/  
│   ├── migrate-original-data.ts  
│   ├── verify-migration.ts  
│   ├── seed-demo-data.ts  
│   ├── build-release.ts  
│   └── verify-release.ts  
│  
├── tests/  
│   ├── unit/  
│   ├── integration/  
│   ├── e2e/  
│   ├── gst/  
│   ├── migration/  
│   ├── security/  
│   └── sync/  
│  
├── docs/  
│   ├── architecture/  
│   ├── database/  
│   ├── api/  
│   ├── features/  
│   ├── security/  
│   ├── deployment/  
│   └── user-guides/  
│  
├── .env.example  
├── .gitignore  
├── docker-compose.yml  
├── package.json  
├── pnpm-workspace.yaml  
├── pnpm-lock.yaml  
└── README.md

Architecture recommendation: Start with a modular monolith for the cloud backend, not 15 microservices. Separate modules logically and deploy the API and workers independently. You can split high-load services later.  
7\. Complete database design  
VentureBill needs two databases:  
1\. PostgreSQL for the cloud.  
2\. SQLite for the desktop.  
Both databases should use compatible identifiers, transaction concepts and synchronization metadata.  
7.1 Database design principles  
Every business record should have:  
\- UUID primary key.  
\- Tenant ownership.  
\- Company ownership.  
\- Branch ownership where applicable.  
\- Created timestamp.  
\- Updated timestamp.  
\- Created-by user.  
\- Updated-by user.  
\- Version number.  
\- Synchronization status or event reference.  
\- Deletion/archive information where applicable.  
For financial records, use immutable transaction history and correction records instead of silently overwriting issued documents.

Use NUMERIC/decimal values for money and quantities where precision matters. Never use floating-point arithmetic for financial calculations.  
7.2 Authentication and organization tables  
Table	Important columns  
tenants	id, name, slug, status, plan\_id  
users	id, name, email, password\_hash, status  
tenant\_memberships	id, tenant\_id, user\_id, status  
roles	id, tenant\_id, name  
permissions	id, code, description  
role\_permissions	role\_id, permission\_id  
membership\_roles	membership\_id, role\_id  
user\_sessions	id, user\_id, refresh\_token\_hash, expires\_at  
companies	id, tenant\_id, legal\_name, GSTIN, PAN, state\_code  
branches	id, tenant\_id, company\_id, name, address  
devices	id, tenant\_id, branch\_id, device\_name, status  
subscriptions	id, tenant\_id, plan\_id, status, expires\_at

Relationship  
TENANT  
  \|  
  \+-- MEMBERSHIPS  
  \|      \|  
  \|      \+-- USERS  
  \|      \+-- ROLES  
  \|             \|  
  \|             \+-- PERMISSIONS  
  \|  
  \+-- COMPANIES  
         \|  
         \+-- BRANCHES  
                \|  
                \+-- DEVICES

A user can belong to multiple tenants, but access must be explicitly granted for each tenant.  
7.3 Customer and supplier tables  
Table	Important columns  
customers	id, tenant\_id, company\_id, name, GSTIN, PAN, phone, email  
customer\_addresses	id, customer\_id, type, address, state\_code, pincode  
customer\_contacts	id, customer\_id, name, phone, email  
suppliers	id, tenant\_id, company\_id, name, GSTIN, phone, email  
supplier\_addresses	id, supplier\_id, address, state\_code, pincode  
customer\_credit\_limits	id, customer\_id, limit\_amount, current\_exposure

Do not make the customer table globally shared between unrelated tenants.  
7.4 Products and inventory  
Table	Purpose  
product\_categories	Product grouping  
products	Product and service catalog  
product\_units	Units of measurement  
product\_tax\_profiles	GST classification  
warehouses	Stock locations  
stock\_balances	Current calculated stock  
stock\_movements	Append-only stock changes  
stock\_adjustments	Corrections  
stock\_transfers	Warehouse transfers  
stock\_transfer\_items	Transferred quantities  
boms	Bill of Materials  
bom\_items	Components of finished goods  
production\_orders	Production records  
production\_items	Output and input materials  
stock\_batches	Optional batch tracking

Important: stock\_balances is a projection of stock\_movements. The movement ledger is the source of truth.

Example:  
Opening stock             \+100  
Purchase                   \+50  
Sales                      \-20  
Sales return                \+5  
Stock adjustment            \-2  
\--------------------------------  
Closing stock              133

7.5 Sales and invoicing tables  
Table	Purpose  
document\_sequences	Invoice numbering  
invoices	Invoice header  
invoice\_items	Invoice line items  
invoice\_taxes	Tax breakdown  
invoice\_discounts	Discounts  
invoice\_notes	Internal/public notes  
invoice\_terms	Terms snapshot  
invoice\_attachments	Attachments  
invoice\_cancellations	Cancellation records  
credit\_notes	Credit note header  
credit\_note\_items	Credit note items  
delivery\_challans	Delivery documents  
quotations	Estimates/proforma  
quotation\_items	Estimate items

Invoice table design  
A suggested structure:  
invoices  
\--------  
id UUID PRIMARY KEY  
tenant\_id UUID NOT NULL  
company\_id UUID NOT NULL  
branch\_id UUID  
customer\_id UUID  
document\_type  
document\_number  
financial\_year  
document\_date  
due\_date  
place\_of\_supply  
supply\_type  
currency\_code  
exchange\_rate  
taxable\_amount  
discount\_amount  
cgst\_amount  
sgst\_amount  
utgst\_amount  
igst\_amount  
cess\_amount  
round\_off  
total\_amount  
paid\_amount  
balance\_amount  
status  
version  
created\_at  
updated\_at  
created\_by

Critical database constraints  
\- Unique invoice number within the correct company, branch and numbering series.  
\- Invoice totals must match their item and tax totals.  
\- Currency and exchange-rate snapshots must be retained.  
\- An issued invoice should not be silently overwritten.  
\- A cancelled invoice number must never be reused.  
\- Credit notes must reference their original invoice when required.  
\- GST snapshots must retain the original tax rates and calculation context.  
7.6 Payments and finance  
Table	Purpose  
payments	Money received or paid  
payment\_allocations	Allocate payment against invoices  
receipts	Receipt documents  
expenses	Expense header  
expense\_items	Expense details  
expense\_taxes	Expense GST  
cash\_accounts	Cash accounts  
bank\_accounts	Bank accounts  
cash\_transactions	Cash movement  
bank\_transactions	Bank movement  
bank\_reconciliations	Reconciliation records  
financial\_periods	Financial-year periods

Payments should be stored separately from invoices.

Example: A customer pays ₹10,000 against an invoice of ₹25,000.  
Invoice total       ₹25,000  
Payment received    ₹10,000  
Outstanding         ₹15,000

A second payment should create another payment record, not overwrite the first payment.  
7.7 Purchase management  
Table	Purpose  
purchase\_orders	Supplier order  
purchase\_order\_items	Order items  
purchase\_bills	Supplier invoices  
purchase\_bill\_items	Purchase items  
supplier\_payments	Supplier payments  
supplier\_payment\_allocations	Allocate payments  
purchase\_returns	Purchase returns  
purchase\_return\_items	Returned items  
goods\_receipts	Received goods  
goods\_receipt\_items	Received quantities

7.8 GST and taxation tables  
Table	Purpose  
tax\_rates	Tax-rate configuration  
tax\_components	CGST, SGST, IGST, UTGST, cess  
gst\_registrations	Business GST registrations  
gst\_return\_periods	Return periods  
gst\_return\_snapshots	Frozen return calculations  
gst\_return\_documents	Included documents  
gst\_reconciliations	Reconciliation session  
gst\_reconciliation\_items	Individual matches  
gst\_einvoice\_records	IRN records when integrated  
eway\_bill\_records	E-Way Bill records  
tds\_entries	TDS transactions  
tcs\_entries	TCS transactions  
tax\_rule\_versions	Versioned tax rules

Tax rates and rules should be effective-dated. This avoids old invoices being recalculated using today's rules.  
7.9 Reports, system and synchronization  
Table	Purpose  
audit\_logs	Who changed what  
notifications	Business alerts  
recurring\_templates	Recurring invoices  
recurring\_executions	Generation history  
file\_attachments	Document metadata  
backup\_records	Backup history  
sync\_outbox	Pending events  
sync\_inbox	Processed cloud events  
sync\_cursors	Last synchronized position  
sync\_conflicts	Conflicting changes  
sync\_runs	Sync execution history  
idempotency\_keys	Prevent duplicate operations  
app\_settings	Company settings  
user\_preferences	Personal preferences  
subscription\_plans	Product plans  
subscription\_entitlements	Enabled capabilities

7.10 Recommended database indexes  
At minimum:  
CREATE INDEX idx\_invoices\_tenant\_date  
ON invoices (tenant\_id, document\_date DESC);

CREATE INDEX idx\_invoices\_customer  
ON invoices (tenant\_id, customer\_id);

CREATE INDEX idx\_invoices\_status  
ON invoices (tenant\_id, status);

CREATE INDEX idx\_products\_company  
ON products (tenant\_id, company\_id);

CREATE INDEX idx\_stock\_movements\_product  
ON stock\_movements (tenant\_id, product\_id, created\_at);

CREATE INDEX idx\_payments\_customer  
ON payments (tenant\_id, customer\_id);

CREATE INDEX idx\_audit\_tenant\_date  
ON audit\_logs (tenant\_id, created\_at DESC);

Additionally:  
\- Add composite unique constraints for invoice numbering.  
\- Add foreign keys for ownership relationships.  
\- Use PostgreSQL Row-Level Security as defense in depth.  
\- Add indexes to synchronization event IDs.  
\- Add unique idempotency constraints.  
Do not rely on Row-Level Security alone. Application authorization must still validate tenant, company and branch access.  
8\. Complete API design  
Use a versioned REST API:  
/api/v1/

All cloud API endpoints should require authentication unless explicitly public.  
8.1 Authentication APIs  
Method	Endpoint	Function  
POST	/auth/register	Create account  
POST	/auth/login	Login  
POST	/auth/refresh	Refresh session  
POST	/auth/logout	Logout  
POST	/auth/forgot-password	Password recovery  
POST	/auth/reset-password	Reset password  
GET	/auth/me	Current user

8.2 Organization APIs  
Method	Endpoint	Function  
GET	/tenants	List accessible tenants  
POST	/tenants	Create tenant  
GET	/companies	List companies  
POST	/companies	Create company  
PATCH	/companies/:id	Update company  
GET	/branches	List branches  
POST	/branches	Create branch  
GET	/users	List users  
POST	/users/invite	Invite user  
PATCH	/users/:id/roles	Assign roles

8.3 Dashboard APIs  
GET /api/v1/dashboard/summary  
GET /api/v1/dashboard/sales-chart  
GET /api/v1/dashboard/purchase-chart  
GET /api/v1/dashboard/outstanding  
GET /api/v1/dashboard/low-stock  
GET /api/v1/dashboard/recent-transactions  
GET /api/v1/dashboard/notifications

Dashboard data should respect the user's permissions and selected company/branch.  
8.4 Sales and invoice APIs  
GET    /api/v1/invoices  
POST   /api/v1/invoices  
GET    /api/v1/invoices/:id  
PATCH  /api/v1/invoices/:id  
POST   /api/v1/invoices/:id/issue  
POST   /api/v1/invoices/:id/cancel  
POST   /api/v1/invoices/:id/duplicate  
POST   /api/v1/invoices/:id/payments  
GET    /api/v1/invoices/:id/pdf  
GET    /api/v1/invoices/:id/history

Also:  
GET    /api/v1/quotations  
POST   /api/v1/quotations  
POST   /api/v1/quotations/:id/convert

GET    /api/v1/credit-notes  
POST   /api/v1/credit-notes

GET    /api/v1/delivery-challans  
POST   /api/v1/delivery-challans

Example invoice creation request  
{  
  "companyId": "uuid",  
  "branchId": "uuid",  
  "documentType": "TAX\_INVOICE",  
  "customerId": "uuid",  
  "documentDate": "2026-11-11",  
  "placeOfSupply": "24",  
  "currencyCode": "INR",  
  "items": \[  
    {  
      "productId": "uuid",  
      "description": "Product A",  
      "quantity": "2",  
      "unit": "PCS",  
      "rate": "1000.00",  
      "discount": "0.00",  
      "taxRate": "18"  
    }  
  \]  
}

The server should calculate the official totals using the shared invoice engine. Do not trust client-submitted totals.  
8.5 Customer and supplier APIs  
GET    /api/v1/customers  
POST   /api/v1/customers  
GET    /api/v1/customers/:id  
PATCH  /api/v1/customers/:id  
DELETE /api/v1/customers/:id  
GET    /api/v1/customers/:id/ledger  
GET    /api/v1/customers/:id/outstanding

GET    /api/v1/suppliers  
POST   /api/v1/suppliers  
GET    /api/v1/suppliers/:id  
PATCH  /api/v1/suppliers/:id  
GET    /api/v1/suppliers/:id/ledger

Deletion should be restricted when records are referenced by historical transactions. Prefer archive/deactivation.  
8.6 Inventory APIs  
GET  /api/v1/products  
POST /api/v1/products  
GET  /api/v1/products/:id  
PATCH /api/v1/products/:id

GET  /api/v1/inventory/stock  
GET  /api/v1/inventory/movements  
POST /api/v1/inventory/adjustments  
POST /api/v1/inventory/transfers

GET  /api/v1/warehouses  
POST /api/v1/warehouses

GET  /api/v1/manufacturing/boms  
POST /api/v1/manufacturing/boms  
POST /api/v1/manufacturing/production-orders  
POST /api/v1/manufacturing/production-orders/:id/complete

8.7 Purchase APIs  
GET  /api/v1/purchases  
POST /api/v1/purchases  
GET  /api/v1/purchases/:id  
PATCH /api/v1/purchases/:id

GET  /api/v1/purchase-orders  
POST /api/v1/purchase-orders  
POST /api/v1/purchase-orders/:id/receive  
POST /api/v1/purchase-orders/:id/convert

POST /api/v1/supplier-payments  
GET  /api/v1/supplier-payments

8.8 Finance APIs  
GET  /api/v1/expenses  
POST /api/v1/expenses  
PATCH /api/v1/expenses/:id

GET  /api/v1/payments  
POST /api/v1/payments  
POST /api/v1/payments/:id/allocate

GET  /api/v1/receipts  
POST /api/v1/receipts

GET  /api/v1/cash-book  
POST /api/v1/cash-book  
GET  /api/v1/bank-accounts  
POST /api/v1/bank-accounts

8.9 GST APIs  
GET  /api/v1/gst/summary  
GET  /api/v1/gst/returns/periods

POST /api/v1/gst/gstr1/generate  
GET  /api/v1/gst/gstr1/:id/export

POST /api/v1/gst/gstr3b/generate  
GET  /api/v1/gst/gstr3b/:id/export

POST /api/v1/gst/gstr2b/import  
POST /api/v1/gst/gstr2b/reconcile  
GET  /api/v1/gst/gstr2b/reconcile/:id

POST /api/v1/gst/eway-bill/export  
GET  /api/v1/gst/tds/report  
GET  /api/v1/gst/tcs/report

All generated return data should preserve its period, source transactions, calculation version and export history.  
8.10 Synchronization APIs  
These are essential to the hybrid architecture.  
POST /api/v1/devices/register  
GET  /api/v1/devices

POST /api/v1/sync/push  
GET  /api/v1/sync/pull  
GET  /api/v1/sync/status

POST /api/v1/sync/acknowledge  
GET  /api/v1/sync/conflicts  
POST /api/v1/sync/conflicts/:id/resolve

Example sync event:  
{  
  "eventId": "uuid",  
  "deviceId": "uuid",  
  "eventType": "invoice.created",  
  "aggregateId": "uuid",  
  "aggregateVersion": 1,  
  "occurredAt": "2026-11-11T12:00:00Z",  
  "payload": {  
    "invoiceId": "uuid",  
    "documentNumber": "VB-001"  
  }  
}

Every event needs an idempotency mechanism. Retrying the same event must not create a second invoice or payment.  
8.11 Administrative APIs  
GET  /api/v1/admin/dashboard  
GET  /api/v1/admin/tenants  
GET  /api/v1/admin/subscriptions  
POST /api/v1/admin/subscriptions  
GET  /api/v1/admin/releases  
POST /api/v1/admin/releases  
GET  /api/v1/admin/audit-logs  
GET  /api/v1/admin/support-tickets

Only VentureBill's authorized internal administrators should access these endpoints.  
9\. Role-based access control  
VentureBill should support different roles.  
Role	Permissions  
Super Admin	VentureBill platform administration  
Business Owner	Complete access to own tenant  
Company Admin	Company-level administration  
Branch Manager	Branch-level operations  
Accountant	Invoices, GST, finance, reports  
Cashier	Billing, receipts, payments  
Sales Executive	Customers, quotations, sales  
Inventory Manager	Products, stock, purchases  
Purchase Manager	Suppliers, purchase orders  
Auditor	Read-only financial records  
Employee	Explicitly assigned access

Example permission codes  
dashboard.view

invoice.view  
invoice.create  
invoice.edit\_draft  
invoice.issue  
invoice.cancel  
invoice.delete\_draft

customer.view  
customer.create  
customer.edit

inventory.view  
inventory.adjust  
inventory.transfer

purchase.view  
purchase.create  
purchase.approve

gst.view  
gst.generate  
gst.export

report.view  
report.export

user.view  
user.invite  
user.assign\_role

settings.view  
settings.manage

A cashier should not be able to change the GST configuration or delete historical invoices.

Permissions should be enforced at the API layer and checked again in the UI for a good user experience.  
10\. Development phases and milestones  
I recommend an incremental implementation with clear acceptance criteria.

The following is a realistic planning estimate for a small, experienced development team. It is not a promise of delivery time; actual duration depends heavily on the recovered frontend source, migration complexity and testing.  
VentureBill development roadmap  
Total estimated duration  
28–40 weeks  
Indicative schedule with overlapping workstreams and validation gates.  
Phase	Deliverable  
0	Source recovery and audit  
1	VentureBill foundation  
2	Branding and UI  
3	Database and cloud API  
4	Authentication and permissions  
5	Billing and GST  
6	Business modules  
7	Electron desktop  
8	Offline synchronization  
9	Backup and security  
10	Reports and integrations  
11	Migration and QA  
12	Commercial release

Phase 0 — Source recovery and baseline audit  
Estimated: 1–2 weeks.

Tasks:  
\- Recover original source.  
\- Verify exact version.  
\- Inventory components.  
\- Inventory APIs.  
\- Identify business logic.  
\- Identify original test cases.  
\- Document current storage.  
\- Create feature matrix.  
\- Create baseline test data.  
\- Verify MIT and dependency licenses.  
Acceptance criteria:  
\- Original project starts successfully.  
\- Original business modules are documented.  
\- GST calculations have baseline tests.  
\- No original code is overwritten.  
\- VentureBill repository exists.  
Phase 1 — VentureBill foundation  
Estimated: 1–2 weeks.

Tasks:  
\- Monorepo setup.  
\- TypeScript configuration.  
\- React application.  
\- Electron application shell.  
\- Node.js API foundation.  
\- PostgreSQL connection.  
\- SQLite connection.  
\- Environment configuration.  
\- Logging.  
\- Error handling.  
\- Shared packages.  
Acceptance:  
\- Web app runs.  
\- Desktop app runs.  
\- Cloud API responds.  
\- Local database works.  
\- Automated tests execute.  
Phase 2 — Branding and design system  
Estimated: 2–3 weeks.

Tasks:  
\- VentureBill identity.  
\- Logo and icons.  
\- Design tokens.  
\- Sidebar.  
\- Header.  
\- Dashboard.  
\- Login.  
\- Responsive layouts.  
\- Tables.  
\- Forms.  
\- Modal system.  
\- Notification system.  
Phase 3 — Cloud database and backend  
Estimated: 3–5 weeks.

Tasks:  
\- Database schema.  
\- Migrations.  
\- Tenant isolation.  
\- Company and branch management.  
\- API modules.  
\- Validation.  
\- Transactions.  
\- Audit events.  
\- Database indexes.  
Phase 4 — Authentication and permissions  
Estimated: 2 weeks.

Tasks:  
\- Registration.  
\- Login.  
\- Sessions.  
\- Password reset.  
\- Device registration.  
\- User invitations.  
\- Role management.  
\- Permission middleware.  
\- Session revocation.  
Phase 5 — Billing and GST engine  
Estimated: 4–5 weeks.

Tasks:  
\- Invoice engine.  
\- Tax calculation.  
\- Discounts.  
\- Numbering.  
\- Credit notes.  
\- Cancellations.  
\- PDF engine.  
\- Thermal printing.  
\- GSTR-1.  
\- GSTR-3B.  
\- GSTR-2B.  
\- E-Way Bill exports.  
\- TDS/TCS.  
Acceptance:  
\- Original test cases pass or have verified equivalents.  
\- New regression tests pass.  
\- GST calculations are reviewed by a qualified professional.  
\- Invoice PDF and thermal outputs match validated expectations.  
Phase 6 — Business modules  
Estimated: 4–5 weeks.

Tasks:  
\- Customers.  
\- Suppliers.  
\- Products.  
\- Inventory.  
\- Warehouses.  
\- Purchases.  
\- Purchase orders.  
\- Expenses.  
\- Payments.  
\- Receipts.  
\- Cash book.  
\- Manufacturing.  
\- Recurring billing.  
Phase 7 — Desktop and printing  
Estimated: 2–3 weeks.

Tasks:  
\- Electron integration.  
\- Secure IPC.  
\- Local API.  
\- SQLite operations.  
\- Printer discovery.  
\- USB and network printer testing.  
\- PDF printing.  
\- Installer.  
\- Auto-update.  
Phase 8 — Offline synchronization  
Estimated: 3–5 weeks.

Tasks:  
\- Outbox/inbox.  
\- Event IDs.  
\- Idempotency.  
\- Device registration.  
\- Conflict resolution.  
\- Stock event synchronization.  
\- Invoice synchronization.  
\- Retry handling.  
\- Sync monitoring.  
This phase should not be rushed.  
Phase 9 — Security and backups  
Estimated: 2 weeks.

Tasks:  
\- Encryption.  
\- Secure sessions.  
\- Tenant isolation tests.  
\- Audit logs.  
\- Backup encryption.  
\- Restore verification.  
\- Update signature verification.  
\- Dependency scanning.  
Phase 10 — Reports and integrations  
Estimated: 2–3 weeks.

Tasks:  
\- P\&L.  
\- Outstanding.  
\- Aging.  
\- Stock valuation.  
\- Product analytics.  
\- Customer analytics.  
\- OCR.  
\- WhatsApp integration.  
\- Email.  
\- Payment integrations.  
Phase 11 — Data migration and quality assurance  
Estimated: 2–3 weeks.

Tasks:  
\- JSON-to-SQLite migration.  
\- SQLite-to-PostgreSQL synchronization.  
\- Data integrity validation.  
\- Duplicate detection.  
\- GST regression.  
\- Load testing.  
\- Printer testing.  
\- Security testing.  
\- Recovery testing.  
Phase 12 — Commercial release  
Estimated: 1–2 weeks.

Tasks:  
\- Signed installer.  
\- Product website.  
\- Documentation.  
\- License notices.  
\- Subscription setup.  
\- Support process.  
\- Monitoring.  
\- Release notes.  
\- Pilot customer deployment.  
11\. Development prompts — complete implementation prompt library  
These prompts are designed to be used sequentially with an AI coding agent such as Codex, ChatGPT Work, Cursor or another repository-aware development agent.

Important: Do not give an AI agent all the prompts at once. Execute one phase, inspect its changes, run tests and approve the result before continuing.

Each prompt tells the agent what to inspect, what to implement and what not to break.  
Prompt 0 — Master project instruction  
Use this as the permanent project instruction.  
:::writing{variant="document" id="73101"}  
\# VENTUREBILL — MASTER DEVELOPMENT INSTRUCTIONS

You are the Principal Software Architect, Senior Full-Stack Engineer, Database Architect, GST Domain Engineer, Desktop Application Engineer and QA Lead for VentureBill.

\#\# Product objective

Transform the original Free GST Billing Software into an independent commercial hybrid business management and GST billing platform named VentureBill.

VentureBill must support:  
\- Windows desktop application.  
\- Web application.  
\- Offline billing.  
\- Cloud synchronization.  
\- Multi-tenant SaaS architecture.  
\- Multiple companies and branches.  
\- Multi-user authentication.  
\- Role-based permissions.  
\- Indian GST billing.  
\- Inventory and accounting workflows.

\#\# Source reuse requirements

1\. Preserve the useful business functionality of the original project.  
2\. Recover and inspect the exact original source version before making changes.  
3\. Never assume files exist unless verified.  
4\. Preserve the original MIT license and copyright notices.  
5\. Do not copy third-party assets without verifying their licenses.  
6\. Never remove a feature without documenting its dependencies and replacement.  
7\. Never replace financial logic with approximate implementations.  
8\. Maintain original functionality through regression tests.

\#\# Architecture

Frontend: React \+ TypeScript \+ Vite.

Desktop: Electron.

Backend: Node.js \+ TypeScript \+ Express or NestJS.

Cloud database: PostgreSQL.

Local database: SQLite.

ORM: Prisma for PostgreSQL, with a compatible SQLite persistence layer.

Cache and jobs: Redis and background workers.

PDF: jsPDF/PDF-lib where appropriate.

OCR: Tesseract.js.

Validation: Zod.

Testing: Vitest, integration tests and Playwright.

\#\# Engineering rules

\- Use modular architecture.  
\- Use TypeScript strict mode.  
\- Use decimal-safe financial arithmetic.  
\- Never trust frontend-calculated invoice totals.  
\- Use database transactions for financial operations.  
\- Enforce tenant isolation on every protected API.  
\- Implement server-side role authorization.  
\- Maintain immutable financial history.  
\- Use idempotency for payments and synchronization.  
\- Maintain an append-only stock movement ledger.  
\- Do not silently overwrite issued invoices.  
\- Implement secure offline authentication.  
\- Protect Electron IPC.  
\- Never expose database credentials to the frontend.  
\- Never expose Electron privileged APIs to the renderer.  
\- Use migrations for schema changes.  
\- Maintain automated tests.  
\- Document all API contracts.  
\- Document all environment variables.  
\- Never commit secrets.

\#\# Required workflow

Before every implementation task:

1\. Inspect the existing repository.  
2\. Identify related files.  
3\. Understand dependencies.  
4\. Explain the implementation plan.  
5\. Implement the requested changes.  
6\. Run linting.  
7\. Run relevant tests.  
8\. Run build.  
9\. Report changed files.  
10\. Report known limitations.

\#\# Financial integrity

Preserve and test:  
\- CGST, SGST, UTGST and IGST.  
\- Cess.  
\- Discounts.  
\- Tax-inclusive and exclusive prices.  
\- Reverse charge.  
\- TDS/TCS.  
\- Round-off.  
\- Credit notes.  
\- Customer credit.  
\- Payment allocation.  
\- Invoice cancellation.  
\- Stock movements.  
\- GST return calculations.

Use versioned and effective-dated tax rules. Require independent validation of statutory compliance.

\#\# Delivery requirements

Every completed phase must contain:  
\- Working source code.  
\- Database changes.  
\- API changes.  
\- Frontend changes.  
\- Tests.  
\- Documentation.  
\- Deployment implications.  
\- Known limitations.  
\- Acceptance checklist.

Do not claim that a feature is completed unless it is implemented, tested and verified.

Your primary goal is to deliver production-quality VentureBill, not merely generate code that looks complete.  
:::Prompt 1 — Complete original source-code audit  
:::writing{variant="document" id="73102"}  
\# PHASE 0 — VENTUREBILL SOURCE CODE AUDIT

Analyze the complete original Free GST Billing Software repository.

Do not modify any files during the initial audit.

\#\# Tasks

1\. Inspect the complete repository.  
2\. Verify the version against the supplied v1.10.84 archive.  
3\. Identify all frontend components, hooks, utilities and contexts.  
4\. Identify every backend route and service.  
5\. Identify all data-storage mechanisms.  
6\. Identify all business modules.  
7\. Identify all tax calculation functions.  
8\. Identify all invoice generation and printing logic.  
9\. Identify all backup and restoration logic.  
10\. Identify all external services and network requests.  
11\. Identify all installer and update mechanisms.  
12\. Identify all dependencies and their licenses.  
13\. Inspect all automated tests.  
14\. Identify unfinished and disabled functionality.  
15\. Identify hardcoded original branding.  
16\. Identify original author-specific links and promotional information.

\#\# Required output

Create:

docs/audit/  
\- 00\_repository\_inventory.md  
\- 01\_architecture\_analysis.md  
\- 02\_frontend\_component\_inventory.md  
\- 03\_backend\_api\_inventory.md  
\- 04\_database\_storage\_analysis.md  
\- 05\_gst\_engine\_analysis.md  
\- 06\_invoice\_engine\_analysis.md  
\- 07\_security\_audit.md  
\- 08\_dependency\_license\_audit.md  
\- 09\_feature\_matrix.md  
\- 10\_migration\_risk\_register.md  
\- 11\_original\_to\_venturebill\_mapping.md

For every identified feature, report:  
\- Existing implementation.  
\- Relevant source file.  
\- Dependencies.  
\- API.  
\- Data model.  
\- Tests.  
\- Migration requirements.  
\- Known limitations.

Do not invent missing files or claim implementation based solely on documentation.

Finish with a prioritized implementation recommendation.  
:::Prompt 2 — Create the VentureBill monorepo  
:::writing{variant="document" id="73103"}  
\# PHASE 1 — VENTUREBILL PROJECT FOUNDATION

Create the new VentureBill monorepo using the architecture approved in the master instructions.

\#\# Workspace

Create:  
\- apps/web  
\- apps/desktop  
\- apps/admin  
\- services/api  
\- services/worker  
\- packages/shared-types  
\- packages/validation  
\- packages/gst-engine  
\- packages/invoice-engine  
\- packages/accounting-engine  
\- packages/inventory-engine  
\- packages/pdf-engine  
\- packages/sync-engine  
\- packages/ui  
\- database/prisma  
\- database/sqlite  
\- tests  
\- docs  
\- infrastructure

Use pnpm workspaces.

Configure:  
\- TypeScript strict mode.  
\- ESLint.  
\- Prettier.  
\- Environment validation.  
\- Centralized logging.  
\- Error handling.  
\- Unit testing.  
\- Integration testing.  
\- Playwright.  
\- Git ignore.  
\- CI pipeline.

Create development, test and production environment templates.

\#\# Requirements

The frontend, desktop application, cloud API and worker must run independently.

The shared packages must not depend on browser-specific or Electron-specific APIs.

Create health-check endpoints.

Create a simple VentureBill dashboard placeholder.

\#\# Deliverables

\- Working monorepo.  
\- README.  
\- Architecture document.  
\- Environment example.  
\- Installation commands.  
\- Build commands.  
\- Test commands.  
\- CI configuration.

Run all builds and tests before completing.  
:::Prompt 3 — VentureBill branding and UI redesign  
:::writing{variant="document" id="73104"}  
\# PHASE 2 — VENTUREBILL BRANDING AND UI/UX

Redesign the application using the VentureBill brand.

Product: VentureBill.

Positioning: Complete GST Billing and Business Management Software.

\#\# Tasks

1\. Remove original product branding from the application UI.  
2\. Create a VentureBill logo and icon system.  
3\. Replace application titles and metadata.  
4\. Create a design system.  
5\. Redesign sidebar and navigation.  
6\. Redesign dashboard.  
7\. Redesign invoice creation.  
8\. Redesign customer management.  
9\. Redesign inventory.  
10\. Redesign purchase management.  
11\. Redesign finance.  
12\. Redesign GST screens.  
13\. Redesign reports.  
14\. Redesign settings.  
15\. Add responsive layouts.

\#\# Design requirements

\- Professional Indian business software.  
\- Clean dashboard.  
\- Consistent spacing.  
\- Accessible contrast.  
\- Responsive tables.  
\- Keyboard navigation.  
\- Light and dark themes.  
\- Reusable components.  
\- Consistent forms and modals.  
\- Fast invoice creation.  
\- Minimal unnecessary animation.

Use the VentureBill identity consistently across desktop, web, PDFs, installers and documentation.

Do not change business calculations or API behavior in this phase.

\#\# Deliverables

Create:  
\- Brand guidelines.  
\- Design tokens.  
\- Component library.  
\- Navigation.  
\- Page layouts.  
\- Responsive UI.  
\- Storybook or equivalent component documentation if practical.

Verify that all existing useful modules remain accessible.  
:::Prompt 4 — PostgreSQL and SQLite database  
:::writing{variant="document" id="73105"}  
\# PHASE 3 — VENTUREBILL DATABASE IMPLEMENTATION

Implement the complete VentureBill database architecture.

\#\# Cloud database

PostgreSQL with Prisma.

\#\# Desktop database

SQLite with versioned migrations.

\#\# Required domains

\- Tenants.  
\- Users.  
\- Memberships.  
\- Roles.  
\- Permissions.  
\- Companies.  
\- Branches.  
\- Devices.  
\- Customers.  
\- Suppliers.  
\- Products.  
\- Categories.  
\- Units.  
\- Warehouses.  
\- Stock movements.  
\- Stock balances.  
\- Invoices.  
\- Invoice items.  
\- Invoice taxes.  
\- Credit notes.  
\- Quotations.  
\- Delivery challans.  
\- Payments.  
\- Payment allocations.  
\- Receipts.  
\- Purchases.  
\- Purchase orders.  
\- Production.  
\- Expenses.  
\- Cash book.  
\- Bank accounts.  
\- GST returns.  
\- GST reconciliation.  
\- Recurring invoices.  
\- Notifications.  
\- Audit logs.  
\- Subscriptions.  
\- Sync outbox.  
\- Sync inbox.  
\- Sync conflicts.  
\- Backups.

\#\# Requirements

1\. Use UUID primary keys.  
2\. Enforce foreign keys.  
3\. Add tenant ownership.  
4\. Add company and branch ownership.  
5\. Use precise numeric monetary fields.  
6\. Add effective-dated tax configuration.  
7\. Add financial document numbering constraints.  
8\. Use transactions for financial operations.  
9\. Implement soft deletion only where appropriate.  
10\. Preserve issued document history.  
11\. Implement migration rollback procedures.  
12\. Add required indexes.  
13\. Add database seed scripts.  
14\. Implement tenant isolation.  
15\. Add audit metadata.

\#\# Deliverables

\- Prisma schema.  
\- SQLite schema.  
\- Migrations.  
\- Seed data.  
\- ER diagram.  
\- Database dictionary.  
\- Migration instructions.  
\- Automated database tests.

Do not proceed to financial API implementation until the schema passes validation.  
:::Prompt 5 — Authentication and permissions  
:::writing{variant="document" id="73106"}  
\# PHASE 4 — AUTHENTICATION AND RBAC

Implement production-ready authentication and authorization for VentureBill.

\#\# Features

\- Registration.  
\- Login.  
\- Logout.  
\- Refresh sessions.  
\- Password reset.  
\- Email verification.  
\- Tenant invitations.  
\- Company membership.  
\- Device registration.  
\- Session revocation.  
\- Role management.  
\- Permission management.  
\- Audit logs.

\#\# Roles

\- Super Admin.  
\- Business Owner.  
\- Company Admin.  
\- Branch Manager.  
\- Accountant.  
\- Cashier.  
\- Sales Executive.  
\- Inventory Manager.  
\- Purchase Manager.  
\- Auditor.  
\- Employee.

\#\# Security requirements

\- Password hashing using a secure password-hashing algorithm.  
\- Secure refresh-token storage.  
\- HttpOnly secure cookies for web sessions.  
\- CSRF protection where cookie authentication is used.  
\- Rate limiting.  
\- Login attempt controls.  
\- Tenant-level authorization.  
\- Branch-level authorization.  
\- Device/session revocation.  
\- No plaintext credentials.  
\- No frontend-only permission checks.

For Electron, establish a secure local authentication model and explicitly documented offline session expiration policy.

\#\# Tests

Test cross-tenant access, privilege escalation, expired sessions, revoked sessions and unauthorized API requests.

Deliver API documentation, permission matrix and security tests.  
:::Prompt 6 — Billing and GST engine migration  
:::writing{variant="document" id="73107"}  
\# PHASE 5 — VENTUREBILL BILLING AND GST ENGINE

Migrate and modernize the original billing and GST functionality.

This is a high-priority financial module.

\#\# Preserve

\- Tax Invoice.  
\- Proforma/Estimate.  
\- Bill of Supply.  
\- Credit Note.  
\- Delivery Challan.  
\- Invoice numbering.  
\- GSTIN validation.  
\- HSN/SAC.  
\- Units of measurement.  
\- CGST.  
\- SGST.  
\- UTGST.  
\- IGST.  
\- Cess.  
\- SEZ handling.  
\- Place of supply.  
\- Reverse charge.  
\- Tax-inclusive pricing.  
\- Tax-exclusive pricing.  
\- Four discount modes.  
\- Invoice-level discount.  
\- Round-off.  
\- TDS.  
\- TCS.  
\- Multi-currency.  
\- Exchange-rate snapshots.  
\- UPI QR.  
\- Amount in words.  
\- Cancellation.  
\- Credit balance.  
\- Invoice-to-payment reconciliation.

\#\# GST modules

\- GSTR-1.  
\- GSTR-3B.  
\- GSTR-2B reconciliation.  
\- HSN summaries.  
\- B2B/B2C summaries.  
\- Credit/debit notes.  
\- E-Way Bill export.  
\- TDS/TCS reports.  
\- Filing assistance.

\#\# Requirements

1\. Extract business logic from the original implementation.  
2\. Preserve original test fixtures.  
3\. Build a centralized tax engine.  
4\. Use decimal-safe arithmetic.  
5\. Version tax rules.  
6\. Store calculation snapshots.  
7\. Validate tax outputs.  
8\. Create regression tests.  
9\. Generate PDF invoices.  
10\. Support A4 and thermal printing.  
11\. Preserve historical invoice numbers.  
12\. Implement appropriate cancellation and credit-note workflows.

Do not invent GST statutory rules.

Validate relevant legal requirements using current authoritative GST and tax sources and qualified professional review.

\#\# Acceptance

All financial test cases must pass.

Every invoice calculation must be reproducible from its stored inputs and tax-rule version.  
:::Prompt 7 — Business modules  
:::writing{variant="document" id="73108"}  
\# PHASE 6 — VENTUREBILL BUSINESS MANAGEMENT MODULES

Implement all remaining business management functionality.

\#\# Customer management

Customer CRUD, GSTIN, contacts, addresses, ledgers, outstanding and credit limits.

\#\# Supplier management

Supplier records, GSTIN, contacts, addresses, purchase ledger and outstanding.

\#\# Products

Products, services, categories, HSN/SAC, tax rates, units, pricing and import/export.

\#\# Inventory

Stock balances, movements, stock adjustment, low stock, warehouses, transfers, stock valuation and historical reports.

\#\# Purchases

Purchase bills, purchase orders, goods receipt, supplier payments, purchase returns and OCR.

\#\# Manufacturing

Bill of Materials, production orders, raw-material consumption and finished-goods creation.

\#\# Finance

Expenses, receipts, payment allocations, cash book, bank accounts and reconciliation.

\#\# Recurring billing

Recurring templates, schedules, generation history, retry handling and duplicate prevention.

\#\# Reports

Sales, purchases, profit and loss, COGS, outstanding, aging, inventory, customer and supplier reports.

\#\# Requirements

\- Separate service layer.  
\- Database transactions.  
\- Permission checks.  
\- Tenant isolation.  
\- Input validation.  
\- Audit events.  
\- Unit tests.  
\- Integration tests.  
\- UI implementation.  
\- API documentation.

Preserve the original business logic and validate all important calculations.  
:::Prompt 8 — Electron desktop application  
:::writing{variant="document" id="73109"}  
\# PHASE 7 — VENTUREBILL ELECTRON DESKTOP

Create the Windows-first VentureBill desktop application using Electron.

\#\# Requirements

\- Electron main process.  
\- Secure preload.  
\- Context isolation.  
\- Node integration disabled in renderer.  
\- Explicit IPC allowlist.  
\- Local API.  
\- SQLite database.  
\- Local authentication.  
\- Offline billing.  
\- Printer discovery.  
\- USB printing.  
\- Network printing.  
\- A4 PDF printing.  
\- 58mm and 80mm thermal printing.  
\- Multiple printer profiles.  
\- Backup and restoration.  
\- Application update.  
\- Windows installer.

\#\# Security

Never expose unrestricted Node.js access to React.

Validate all IPC payloads.

Do not expose secrets to the renderer.

Use secure storage for credentials where supported.

Protect local database and backup files.

\#\# Offline requirements

A user must be able to create invoices, manage customers, update stock, record purchases and print invoices without internet.

\#\# Deliverables

\- Working Electron application.  
\- Installer.  
\- Printer service.  
\- Local database.  
\- Local API.  
\- Backup service.  
\- Offline authentication.  
\- Installation and recovery documentation.  
:::Prompt 9 — Hybrid synchronization  
:::writing{variant="document" id="73110"}  
\# PHASE 8 — VENTUREBILL HYBRID SYNCHRONIZATION

Implement a reliable offline-first synchronization system between desktop SQLite and cloud PostgreSQL.

\#\# Components

\- Device registration.  
\- Local sync outbox.  
\- Cloud sync inbox.  
\- Event IDs.  
\- Idempotency keys.  
\- Sync cursors.  
\- Push API.  
\- Pull API.  
\- Acknowledgment API.  
\- Retry mechanism.  
\- Conflict detection.  
\- Conflict resolution.  
\- Sync status dashboard.  
\- Sync logs.

\#\# Business rules

1\. Offline invoices must save locally.  
2\. Offline payments must save locally.  
3\. Stock changes must be recorded as movements.  
4\. Financial operations must not silently overwrite one another.  
5\. Duplicate sync events must not duplicate records.  
6\. Failed events must remain retryable.  
7\. Cloud acknowledgments must be persisted.  
8\. Conflicts must be visible and auditable.  
9\. Device identity must be validated.  
10\. Sync must resume after application restart.

\#\# Conflict handling

\- Financial transactions: immutable event processing.  
\- Issued invoices: correction workflows.  
\- Stock: movement-based reconciliation.  
\- Payments: immutable events and allocations.  
\- Customer details: version-based conflict resolution.  
\- Settings: controlled last-write-wins where appropriate.

\#\# Tests

Test:  
\- No internet.  
\- Internet interruption.  
\- Duplicate event.  
\- Partial synchronization.  
\- Application restart.  
\- Database failure.  
\- Concurrent devices.  
\- Duplicate invoice number.  
\- Stock conflict.  
\- Payment conflict.

Deliver an architecture diagram, synchronization protocol and automated tests.  
:::Prompt 10 — Backup, security and deployment  
:::writing{variant="document" id="73111"}  
\# PHASE 9–12 — VENTUREBILL SECURITY AND COMMERCIAL RELEASE

Prepare VentureBill for commercial distribution.

\#\# Security

\- Authentication audit.  
\- Tenant isolation audit.  
\- Permission audit.  
\- Electron security audit.  
\- API rate limiting.  
\- Input validation.  
\- SQL injection prevention.  
\- XSS protection.  
\- CSRF protection.  
\- Secure secrets.  
\- Encryption at rest.  
\- TLS.  
\- Audit logging.  
\- Dependency scanning.  
\- Backup encryption.

\#\# Backup

\- Local automatic backup.  
\- Cloud backup.  
\- Manual backup.  
\- Backup verification.  
\- Restore testing.  
\- Retention policies.  
\- Disaster recovery.  
\- Tenant-specific backup and restore.

\#\# Commercial functionality

\- Subscription plans.  
\- Feature entitlements.  
\- Subscription renewal.  
\- Device limits.  
\- User limits.  
\- Billing and payment integration.  
\- Trial accounts.  
\- Support tickets.  
\- Product updates.  
\- License management.

\#\# Deployment

\- Docker.  
\- PostgreSQL.  
\- Redis.  
\- API deployment.  
\- Worker deployment.  
\- Object storage.  
\- Database migrations.  
\- HTTPS.  
\- Monitoring.  
\- Logging.  
\- Alerting.  
\- Signed desktop installers.  
\- Release management.

\#\# Final acceptance

The software must pass:

1\. Unit tests.  
2\. Integration tests.  
3\. End-to-end tests.  
4\. GST regression tests.  
5\. Database migration tests.  
6\. Tenant-isolation tests.  
7\. Security tests.  
8\. Offline tests.  
9\. Synchronization tests.  
10\. Backup/restore tests.  
11\. Printer tests.  
12\. Production build verification.

Do not mark VentureBill production-ready until all critical tests pass and unresolved risks are documented.

Produce a complete release report, installation guide, administrator guide and client handover checklist.  
:::12. Product security requirements  
Before selling VentureBill, implement the following safeguards.  
Area	Requirement  
Passwords	Argon2id or equivalent  
Sessions	Revocable sessions  
Web security	HTTPS, secure cookies, CSRF protection  
API	Authentication, authorization and rate limiting  
Database	Tenant isolation and encryption at rest  
Electron	Context isolation and secure IPC  
Offline data	Protected local database  
Backups	Encrypted and integrity-checked  
Financial history	Auditable transaction records  
Updates	Signed and verified packages  
Monitoring	Errors, uptime and sync failures  
Privacy	Data retention and deletion policies

For offline operation, use a documented grace-period and session policy. A customer's device should not suddenly become unusable when their subscription server is unavailable.  
12.1 Important commercial and legal requirements  
Before launching:  
\- Preserve the original MIT license.  
\- Maintain copyright notices.  
\- Verify every third-party dependency and font license.  
\- Publish VentureBill terms and privacy policy.  
\- Define data ownership and export procedures.  
\- Establish support and refund policies.  
\- Obtain appropriate professional advice on GST and accounting claims.  
\- Validate GST return formats against current GSTN specifications.  
\- Assess applicable Indian data protection obligations.  
\- Do not advertise direct GST filing or e-invoicing until the relevant authorized integrations are actually implemented.  
13\. Deployment architecture  
VentureBill should have three independently managed deployment products.  
13.1 Cloud infrastructure  
Production cloud environment

VentureBill Web Application

React static application · CDN · HTTPS

Cloud API

Node.js · Authentication · Tenant isolation

PostgreSQL

Primary business database

Redis

Queue and cache

Workers

Recurring jobs and sync

Object storage

PDFs and backups

Recommended environments:  
Environment	Purpose  
Development	Local development  
Testing	Automated testing  
Staging	Pre-release validation  
Production	Actual customers

Do not use your production database for development or testing.  
13.2 Desktop distribution  
Build:  
VentureBill-Setup-x64.exe  
VentureBill-Setup-arm64.exe    \# If required  
VentureBill-macOS.dmg  
VentureBill-Linux.AppImage  
VentureBill-Linux.deb

The desktop installer should include:  
\- Electron runtime.  
\- React application.  
\- Local API.  
\- SQLite.  
\- Printer services.  
\- Migration scripts.  
\- Local backup service.  
\- Update service.  
Customer data should be stored outside the installation directory so software upgrades and uninstalls do not accidentally delete business records.  
13.3 Suggested domain structure  
If you purchase a domain, a clean arrangement would be:  
venturebill.com  
    Main product website

app.venturebill.com  
    Customer web application

api.venturebill.com  
    Backend API

admin.venturebill.com  
    Internal administration

docs.venturebill.com  
    Documentation

status.venturebill.com  
    Service status

downloads.venturebill.com  
    Desktop releases

These are proposed domain names, not verified available domains.  
14\. What should be included in the first commercial version?  
Do not wait until every feature is finished to test the product with customers.

I recommend three release levels.

VentureBill V1 — Business Essentials (First release)  
\- Login and business setup.  
\- Customers and suppliers.  
\- Products.  
\- GST invoices.  
\- PDF and thermal printing.  
\- Purchases.  
\- Payments and receipts.  
\- Expenses.  
\- Inventory.  
\- Basic reports.  
\- Local offline database.  
\- Backup and restore.  
\- Basic cloud synchronization.  
VentureBill V2 — Business Management  
\- Multiple branches.  
\- Advanced inventory.  
\- Manufacturing.  
\- Purchase orders.  
\- Recurring invoices.  
\- GST reconciliation.  
\- Advanced reports.  
\- Multiple employees.  
\- Advanced permissions.  
\- Bank reconciliation.  
\- OCR.  
VentureBill V3 — Commercial Enterprise  
\- Subscription management.  
\- Customer portal.  
\- Supplier portal.  
\- Advanced cloud analytics.  
\- WhatsApp Business API.  
\- Payment gateway.  
\- Advanced integrations.  
\- Advanced audit and compliance.  
\- Enterprise administration.  
GSTR-1, GSTR-3B and other essential GST functions should remain in the product's functional scope; release timing should depend on validated compliance and not simply on the version label.  
15\. Definition of Done — VentureBill  
The project is not finished merely because the interface works.

Use this final acceptance checklist.

Release readiness  
/  
\[Reset checklist\]  
16\. My final architectural decisions for VentureBill  
I would lock the following decisions as the project's baseline:  
Decision	Final  
Product	VentureBill  
Architecture	Hybrid, offline-first  
Frontend	React \+ TypeScript  
Desktop	Electron  
Cloud backend	Node.js \+ TypeScript  
API	Modular REST API  
Cloud database	PostgreSQL  
Desktop database	SQLite  
ORM	Prisma for cloud database  
Background jobs	Redis \+ worker  
Sync	Event-based outbox/inbox  
Financial precision	Decimal arithmetic  
GST	Shared, versioned GST engine  
Authorization	RBAC \+ tenant isolation  
Storage	Local \+ cloud object storage  
Printing	PDF \+ USB/network thermal  
Testing	Vitest \+ Playwright  
Deployment	Docker \+ signed desktop installer  
Architecture style	Modular monolith  
Commercial model	Subscription-ready

One especially important decision: Build the cloud API and local desktop API around the same shared business rules. Never maintain two separate GST engines or two separate invoice calculation implementations.

That will save you from a major source of financial inconsistencies.

