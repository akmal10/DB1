# Physician AHCS Database Setup

## Database Information
- **Database Name**: `physician_ahcs`
- **Database System**: MySQL 8.0.43
- **Host**: localhost
- **Port**: 3306
- **User**: root (sudo mysql access)

## Database Structure
The database contains 13 tables with physician and healthcare provider information:

### Main Tables
- `physicians` - 6,017 physician records
- `physician_addresses` - 4,256 address records  
- `physician_histories` - 54,404 history records
- `physician_contacts` - Contact information
- `physician_specialties` - Medical specialties
- `physician_groups` - Group associations
- `physician_ins_types` - Insurance types
- `physician_details` - Additional details
- `physician_providers` - Provider information
- `physician_locations` - Location mappings
- `physician_city_provider_mappings` - City-provider relationships

### New Tables (for migration)
- `physicians_new` - Updated physician structure
- `physician_addresses_new` - Updated address structure

## Connection Examples

### Command Line Access
```bash
sudo mysql physician_ahcs
```

### Basic Queries
```sql
-- View all tables
SHOW TABLES;

-- Count physicians
SELECT COUNT(*) FROM physicians;

-- Sample physician data
SELECT physician_name, specialty, physician_type FROM physicians LIMIT 5;

-- Check table structure
DESCRIBE physicians;
```

## Database Schema Overview

### Physicians Table Structure
- `id` - Primary key (auto increment)
- `physician_name` - Full name (varchar 100)
- `group_id` - Group identifier (varchar 50)
- `last_name`, `first_name` - Name components
- `dob` - Date of birth
- `title` - Professional title
- `license_type`, `license_jurisdiction`, `license_no` - Licensing info
- `specialty` - Medical specialty (text)
- `ins_type` - Insurance type
- `ref_type` - Reference type
- `physician_type` - Type (default: 'External')
- `enable` - Active status (tinyint, default: 1)

## Setup History
- **Source**: phpMyAdmin SQL Dump (7.8MB)
- **Original System**: MySQL 5.6.46
- **Current System**: MySQL 8.0.43 on Ubuntu 22.04
- **Import Date**: September 16, 2025
- **Status**: ✅ Successfully imported and verified

## Verification Results
- ✅ All 13 tables created successfully
- ✅ Data integrity confirmed:
  - 6,017 physicians imported
  - 4,256 addresses imported
  - 54,404 history records imported
- ✅ Database connection tested and working
- ✅ Sample queries executed successfully

## Next Steps for Database Upgrade
1. **Review Migration Strategy**: Examine the relationship between current tables and `*_new` tables
2. **Backup Current Data**: Create backup before upgrade process
3. **Test Migration Scripts**: Validate data migration from old to new table structures
4. **Performance Optimization**: Consider indexing and query optimization for production use
5. **User Management**: Create dedicated database users with appropriate permissions

## Troubleshooting

### Connection Issues
```bash
# Check MySQL service status
sudo systemctl status mysql

# Restart MySQL if needed
sudo systemctl restart mysql
```

### Access Issues
```bash
# Connect as root
sudo mysql

# Switch to database
USE physician_ahcs;
```

## Security Considerations
- Currently using root access for setup
- Consider creating dedicated application user for production
- Implement proper password policies
- Configure firewall rules if accessing remotely

---
*Database setup completed by Devin AI - Session: https://app.devin.ai/sessions/d73d769368e94cc9b01d822bc73ede5a*
*Requested by: akmal10*
