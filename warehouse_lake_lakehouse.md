
**1. Data Warehouse 🏛️**

• Technical Definition: An enterprise database optimized for analytical processing (OLAP) that operates on a rigid Schema-on-Write architecture. Data must be cleaned, transformed, and structured into dimensional models (Star/Snowflake schemas) before ingestion. It enforces database-level ACID compliance to guarantee data consistency.
• Storage Mechanism: Data is stored in a centralized, proprietary storage engine using a compressed, columnar format to optimize aggregation query speed. (Examples: Snowflake, Google BigQuery).
• Netflix Production Example: Subscriber billing and financial transaction records. Transactional records pass through ETL pipelines to validate strict relational constraints before loading. Corporate accounting teams query these immutable tables to generate mathematically flawless, uncorrupted quarterly revenue reports and SEC filings.
Pre-processed and organized data
Schema on write
Data stored after ETL 
For Business Intelligence, Analytics reports
Quality and Consistency for data being reliable
Can be scalable but expensive
EG: Snowflake, bigQry, Redshift, Databricks, ClickHouse

------------------------------------
***2. Data Lake 🌊***

• Technical Definition: A centralized, highly scalable storage repository that ingests and preserves vast amounts of data in its native, unaltered state. It operates on a Schema-on-Read architecture, accepting structured, semi-structured (JSON/XML), and unstructured (videos/images) data without prior validation. The storage layer lacks native compute, requiring external distributed compute frameworks to parse files on demand.
• Storage Mechanism: Data is stored as raw objects or binary files organized within hierarchical directories (prefixes) across distributed nodes. (Examples: Amazon S3, Azure ADLS).
• Netflix Production Example: Raw user-interaction telemetry and app crash logs. Millions of devices stream raw JSON data tracking button clicks, UI hovers, and search strings. This data is dumped directly into object storage buckets partitioned by time, allowing machine learning engineers to connect distributed compute clusters (like Apache Spark) to train personalized artwork recommendation models.
Raw data
Needs no structure to store
Schema on Read 
Effective for high volume of data storage
Flexible  to add diff types/format of data without any new schema 
Low cost
Highly Scalable
Used in AIML/ Data Science tasks on raw data

EG: s3, presto, hive , hadoop

------------------------------------
***3. Data Lakehouse 🏡***
• Technical Definition: An architecture that overlays an open metadata and transaction management layer directly on top of file-based object storage. By maintaining a centralized transaction log, it brings warehouse-level functionalities—including ACID transactions, schema enforcement, mutations (UPSERT/MERGE), and time-travel versioning—directly to raw files, allowing concurrent SQL and machine learning workloads on a single system.
• Storage Mechanism: Data is stored as open-source columnar files (typically Apache Parquet) inside standard cloud object storage, bound together and managed by a metadata transaction log layer. (Examples: Apache Iceberg, Delta Lake).
• Netflix Production Example: Real-time video playback performance metrics. Smart TVs stream playback data (bitrates, buffering delays) into object storage managed by Apache Iceberg. The metadata layer enforces quality schemas in real time, enabling network engineers to run live SQL dashboards monitoring regional bottlenecks while automated optimization algorithms simultaneously query those same files to adjust encoding pipelines and prevent buffering.
	• Unified Storage Architecture (Combines Data Lake flexibility with Data Warehouse reliability).
	• Schema Enforcement & Evolution via a smart metadata layer.
	• ACID Transactions natively on open-source file storage.
	• High-performance SQL querying alongside programmatic data science engines.
	• Decoupled Compute and Storage utilizing open-source table formats.
	• Low Cost & High Scalability (Leverages cheap cloud storage, eliminating data duplication).
	• Supports Concurrent Workloads (Simultaneous BI reporting, data streaming, and AI/ML model training).
• EG: Apache Iceberg, Delta Lake, Apache Hudi, Databricks (Unified Platform
