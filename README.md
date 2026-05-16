# PBIX

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















