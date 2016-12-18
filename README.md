# NativeDSO
SAP HANA Native DSO sample

# Prerequisites

# SQL statements to grant "SBSS" runtime user privileges to activate and delete DSO requests

--find SBSS user

SELECT USER_NAME FROM USERS WHERE USER_NAME like 'SBSS_%';

--grant the SBSS user rights to activate and delete DSO requests

GRANT EXECUTE ON "SYS"."DSO_ACTIVATE_CHANGES" TO SBSS_USER;

GRANT EXECUTE ON "SYS"."DSO_ROLLBACK_CHANGES" TO SBSS_USER;

--improve catalog browsing performance

GRANT CATALOG READ TO SBSS_USER;

--another way to find your SBSS user

select * from granted_roles where UPPER(role_name) like '%<PROJECT_NAME>%' and GRANTEE like 'SBSS_%';
