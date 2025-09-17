📊 Gantt Chart Generator
This is a Python Command-Line Interface (CLI) program designed to automate the creation of high-quality, interactive Gantt Charts. It leverages the powerful Plotly and Pandas libraries to process task data, apply robust validations, and generate dynamic visualizations that can be viewed in a web browser or exported to various formats.
✨ Key Features
* Interactivity: Generates interactive charts with Plotly, allowing users to zoom, pan, and view detailed task information on hover (including Progress, Category, and Dependencies).
* Multiple Data Sources: Supports two methods for data input:
   * Manual: Enter tasks through interactive prompts in the console (--manual).
   * Files: Load data directly from CSV or Excel files (--file).
* Detailed Visualization:
   * Tasks are automatically colored by Category/Group.
   * Displays the Progress percentage directly on the task bar.
   * Visually identifies and marks Milestones with a red diamond symbol (for tasks where the start date equals the end date).
* Dependency Management: Draws basic arrows between tasks to represent Finish-to-Start dependency relationships.
* Data Validation: Includes validation logic to ensure dates are valid, the finish date is on or after the start date, task names are unique, and dependencies exist.
* Flexible Output Formats: Allows you to save the chart in HTML (interactive), PNG, JPG, or SVG format (--output).
🛠️ Requirements and Installation
This program requires Python 3.x and the following libraries.
Library Installation
Use pip to install all necessary dependencies. This includes openpyxl for handling Excel files and kaleido for exporting images (PNG, JPG, SVG).
pip install plotly pandas openpyxl kaleido


🚀 Usage
The main script is designed to be executed from the command line, using the argparse module to manage arguments.
1. File Data Structure
If you choose the file input option, your CSV or Excel file must contain (at a minimum) these columns. The Progress, Dependencies, and Category columns are optional and will be filled with default values if they are missing.
Column
	Description
	Example Format
	Task
	Unique task name
	Interface Design
	Start
	Start date
	2025-01-01, 1/15/2025, etc.
	Finish
	Finish date
	2025-01-10
	Progress
	Percentage complete (optional)
	50 (number between 0 and 100)
	Category
	Project group or phase (optional)
	Planning, Development
	Dependencies
	Names of tasks that this task depends on, separated by commas (optional)
	Task A, Task B
	2. Command-Line Execution
You can choose to enter data manually or load a file. If the --output argument is not specified, the chart will be displayed interactively in your browser.
Manual Input
python gantt_chart_generator.py --manual


(The program will interactively ask you for the number of tasks and details for each one).
File Input (CSV/Excel)
# Example with a CSV file
python gantt_chart_generator.py --file project_data.csv

# Example with an Excel file
python gantt_chart_generator.py --file project_data.xlsx


Saving the Chart
Use the --output argument to save the chart to your disk. The format is automatically inferred from the file extension.
# Save as an interactive HTML file
python gantt_chart_generator.py --file project_data.csv --output interactive_gantt.html

# Save as a PNG image
python gantt_chart_generator.py --manual --output gantt_image.png