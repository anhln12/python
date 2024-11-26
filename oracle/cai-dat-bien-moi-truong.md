**1. Download the Oracle Instant Client**

Go to the Oracle Instant Client downloads page.

Select the appropriate version for Linux x86-64.

Download the following RPM packages:
- oracle-instantclient-basic
- oracle-instantclient-devel (for development headers if needed)
- Optionally, oracle-instantclient-sqlplus (if you need SQL*Plus).

**2. Install the Instant Client RPMs**

Upload the downloaded RPMs to your CentOS 8 machine.

Install the required packages using dnf (or yum):
```
dnf install oracle-instantclient-basic*.rpm oracle-instantclient-devel*.rpm
```

**3. Configure Environment Variables**
Add the Oracle client directory to the LD_LIBRARY_PATH:
```
echo 'export LD_LIBRARY_PATH=/usr/lib/oracle/<version>/client64/lib:$LD_LIBRARY_PATH' >> ~/.bashrc
source ~/.bashrc
```

**4. Install python Libraries**
You need the cx_Oracle Python library to interface with Oracle database
```
pip install cx_Oracle
```

**5. Test the installation**
Create a simple Python script to test the connection:
```
import cx_Oracle

# Replace with your Oracle DB credentials
dsn = cx_Oracle.makedsn("host", port, service_name="service_name")
connection = cx_Oracle.connect(user="username", password="password", dsn=dsn)

print("Connected to Oracle Database:", connection.version)
connection.close()
```
