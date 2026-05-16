# PBIX



Section	Description	Notes

Fact_Orders	Order line fact table with revenue, margin, OTIF, stockout, returns, waste, quality and promo indicators	Core fact table

Inventory_Snapshots	Monthly stock movement and availability indicators by product and warehouse	Inventory fact table

Dim_Product	Product/category/storage/shelf-life attributes	Dimension

Dim_Supplier	Supplier risk, reliability and lead-time attributes	Dimension

Dim_Customer	Customer segment and geography attributes	Dimension

Dim_Warehouse	Warehouse geography, capacity and cold-storage flag	Dimension

Dim_Date	Daily calendar table for date filtering	Date dimension

Dim_Channel	Channel used	Dimension






Fact_Orders -
OrderID	OrderDate	RequiredDate	ShipDate	ProductID	CustomerID	Channel	SupplierID	WarehouseID	OrderQty	UnitPrice	DiscountPct	Revenue	UnitCost	COGS	GrossProfit	OTIF_Flag	LateDays	StockoutFlag	ReturnQty	WasteQty	QualityIssueFlag	PromoFlag

Inventory Snapshot -
SnapshotMonth	ProductID	WarehouseID	OpeningStock	ReceivedQty	ShippedQty	ClosingStock	ReorderPoint	StockoutFlag	ExpiredQty

Dim_Product - 
ProductID	Category	Subcategory	Brand	ProductName	ShelfLifeDays	StorageType	UnitWeightKg	ListPrice	StandardCost

Dim_Supplier - 
SupplierID	SupplierName	SupplierRegion	RiskTier	PlannedLeadTimeDays	ReliabilityPct	AvgDefectRate	City	Country	Latitude	Longitude

Dim_Customer -
CustomerID	CustomerName	CustomerSegment	Country	City	SalesRegion	Priority

Dim_warehouse - 
WarehouseID	WarehouseName	Country	WarehouseRegion	CapacityPallets	ColdStorageFlag















