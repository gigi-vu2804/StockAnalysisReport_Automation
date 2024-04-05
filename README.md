# Stock Analysis and Reporting Automation
@author: gigivu-2804
The `stockreport.ipynb` Python script automates the process of 
- Analyze raw stocks data from a csv file,
- Generate reports on the biggest daily movers and average percentage changes of each stock,
- Store the generated data to a SQL Server (in this case SQLite Database), 
- Generate & save the image of stocks correlation matrix.

This document outlines the steps required to set up and run the script along with its dependencies.

## Dependencies

The script requires the following Python packages:
- `pandas`: For data manipulation and analysis.
- `numpy`: For numerical calculations.
- `sqlalchemy`: For database interaction.
- `matplotlib`: For generating visualizations.
- `seaborn`: For advanced visualizations and heatmaps.

Additionally, the script is designed to interface with an SQLite database, requiring the respective database file set up as per the script configuration.

## Setup

### Install Python

Ensure that Python 3.6 or newer is installed on your system. You can download it from [Python Downloads](https://www.python.org/downloads/).

### Install Dependencies

Run the following command in your terminal or command prompt to install the required Python packages:

```bash
pip install pandas numpy sqlalchemy matplotlib seaborn
```

### Database Setup
Download and set up SQLite for Windows:
#### Download SQLite: 
Visit the [SQLite Download Page](https://www.sqlite.org/download.html) and download the precompiled binaries for Windows. Look for the `sqlite-tools-win32-x86-*.zip` file under the "Precompiled Binaries for Windows" section.

#### Extract the Files: 
Extract the downloaded ZIP file to a directory on your computer, such as C:\sqlite.

#### Add SQLite to Your PATH (Optional):
- Right-click on 'This PC' or 'My Computer' and select 'Properties'.
- Click on 'Advanced system settings' and then 'Environment Variables'.
- Under 'System Variables', find and select 'Path', then click 'Edit'.
- Click 'New' and add the path to the directory where you extracted the SQLite tools (e.g., C:\sqlite).
- Click 'OK' to close the dialog boxes.
- Adding SQLite to your PATH allows you to access it from any command prompt window.

#### Using SQLite with the Script
For SQLite, no additional setup is required as the script will create or use an existing `.db` file as specified. In the main usage of `stockreport.ipynb`, we're using `stock_analysis.db` as the database file path.

### Data Preparation
Place your stock data file (e.g., `stocks.csv`) in the `res` folder within the same directory/folder as the `stockreport.ipynb` file. Ensure the data format aligns with the script's expectations (`Symbol`, `Date`, `Open`, `High`, `Low`, `Close`, `Volume`).


## Running the Script
### Configure the Script
Edit the script or an accompanying configuration file to specify the path to your `stocks.csv` data file and the database file path (for SQLite).

### Execute the Script
To run the `stockreport.ipynb` notebook:

- **Open Your Notebook Environment**: Navigate to your preferred notebook environment. This could be Jupyter Notebook, JupyterLab, or Visual Studio Code with the Jupyter extension installed.

- **Open the Notebook** : Within your notebook environment, navigate to the directory containing `stockreport.ipynb` and open the file.

- **Run the Notebook**: Execute the cells in the notebook in sequence. You can typically run a cell by selecting it and pressing Shift + Enter, or by using the play/run button in the toolbar of your notebook environment.

Ensure all cells are executed in order to perform the complete analysis and generate the required outputs.


## Output
The script will generate:

- **Database Tables** : Data will be saved in specified tables within the SQLite database. the stock_analysis.db file will be stored inside `database` directory/folder
- **Visualization Images**: Correlation matrix images will be saved in the `correlation_matrix` directory/folder

## Open the SQLite Database:

If sqlite3.exe is in your PATH and you are in the directory of your database (e.g. `C:\3. Personal\stockanalysisreport_automation\database\`), simply type:
```bash
sqlite3 stock_analysis.db
```

If sqlite3.exe is in your PATH but you are not in the directory of your database, use the full path to your database file:
```bash
sqlite3 C:\path\to\database\stock_analysis.db
```

If sqlite3.exe is not in your PATH, you need to navigate to the directory where sqlite3.exe is located or specify its full path before the database path:
```bash
C:\path\to\sqlite3 C:\path\to\database\stock_analysis.db
```

### Useful SQL or SQLite-specific commands
List All Tables:
```bash
.tables
```
This command lists all tables in your database.

Schema of a Table:
```bash
.schema tablename
```
Replace tablename with the actual name of your table. This command shows the CREATE statement used to create the table, which includes all column names and types.

Selecting Data:
```sql
SELECT * FROM tablename;
```
This is a SQL query that selects all columns from a specific table. Replace tablename with the name of the table you want to query. Remember to end SQL statements with a semicolon (;).

Exiting SQLite:
```bash
.quit
```
This command exits the SQLite command-line interface and returns you to the CMD prompt.

Getting Help:
```bash
.help
```
This shows a list of all dot commands and a brief description of their functionality.

## Troubleshooting
If you encounter any errors related to database connections, ensure your database file path is correct.
For issues with data formats, verify that your CSV file matches the expected schema.

