🏠 Airbnb End-to-End Data Engineering Project
📋 Overview
This project implements a complete end-to-end data engineering pipeline for Airbnb data using modern cloud technologies. The solution demonstrates best practices in data warehousing, transformation, and analytics using Snowflake, dbt (Data Build Tool), and AWS.

The pipeline processes Airbnb listings, bookings, and hosts data through a medallion architecture (Bronze → Silver → Gold), implementing incremental loading, slowly changing dimensions (SCD Type 2), and creating analytics-ready datasets.

🏗️ Architecture
Data Flow
Source Data (CSV) → AWS S3 → Snowflake (Staging) → Bronze Layer → Silver Layer → Gold Layer
                                                           ↓              ↓           ↓
                                                      Raw Tables    Cleaned Data   Analytics

📊 Data Model
Medallion Architecture
🥉 Bronze Layer (Raw Data)
Raw data ingested from staging with minimal transformations:

bronze_bookings - Raw booking transactions
bronze_hosts - Raw host information
bronze_listings - Raw property listings
🥈 Silver Layer (Cleaned Data)
Cleaned and standardized data:

silver_bookings - Validated booking records
silver_hosts - Enhanced host profiles with quality metrics
silver_listings - Standardized listing information with price categorization
🥇 Gold Layer (Analytics-Ready)
Business-ready datasets optimized for analytics:

obt (One Big Table) - Denormalized fact table joining bookings, listings, and hosts
fact - Fact table for dimensional modeling
Ephemeral models for intermediate transformations
Snapshots (SCD Type 2)
Slowly Changing Dimensions to track historical changes:

dim_bookings - Historical booking changes
dim_hosts - Historical host profile changes
dim_listings - Historical listing changes
