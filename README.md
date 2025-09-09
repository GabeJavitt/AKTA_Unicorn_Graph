ÄKTA Chromatogram Batch PlotterA standalone Python script to automatically batch process ÄKTA UNICORN result .zip files and generate high-quality chromatogram plots. This tool is designed for modern UNICORN 6+ result files and has no external dependency on the PyCORN library.DescriptionThis script provides a simple command-line interface to automate the tedious task of exporting chromatograms. Point it at a folder of your ÄKTA .zip files, and it will generate a .png plot for each one, saving you time and ensuring consistent output for reports and analysis.The core parsing logic for the UNICORN 6 format is integrated directly into the script, so you don't need to install or troubleshoot the PyCORN library.FeaturesBatch Processing: Process an entire folder of .zip files with a single command.Standalone: No PyCORN dependency. The necessary code is built-in.Highly Customizable Plots:Choose exactly which data curves to display (e.g., UV, conductivity, pH).Manually set X and Y-axis limits for standardized, comparable graphs.Smart Defaults: If no curves are specified, the script automatically plots the most common traces (UV, Conductivity, and Gradient).Multi-Axis Support: Automatically creates up to three Y-axes to keep plots with different scales readable.High-Quality Output: Saves plots as 300 DPI .png files suitable for presentations and publications.RequirementsPython 3.xmatplotlibxmltodictSetupClone or Download: Get the batch_chromatogram_plotter.py script from this repository.Install Dependencies: Open your terminal or command prompt and install the required Python libraries using pip.pip install matplotlib xmltodict
UsageRun the script from your terminal. You must provide an input directory (where your .zip files are) and an output directory (where the plots will be saved).Basic Syntaxpython batch_chromatogram_plotter.py <path/to/input_folder> <path/to/output_folder> [options]
Examples1. Default PlottingThis will find all .zip files in the my_results folder and save the plots in my_plots. The script will automatically try to plot the UV, Conductivity, and Concentration B curves.python batch_chromatogram_plotter.py my_results my_plots
2. Plotting Specific CurvesUse the --curves flag to specify which data to plot. Use quotes for names containing spaces.# Plot only the UV 1_280 curve
python batch_chromatogram_plotter.py my_results my_plots --curves "UV 1_280"

# Plot UV 1_280 and the pH curve
python batch_chromatogram_plotter.py my_results my_plots --curves "UV 1_280" "pH"
3. Creating Standardized GraphsUse the --xlim and --ylim flags to set manual axis limits. This is perfect for comparing different runs.# Set the Volume axis from 0-25 mL and the Absorbance axis from 0-500 mAU
python batch_chromatogram_plotter.py my_results my_plots --xlim 0 25 --ylim 0 500
Note: When providing arguments like --curves or --xlim, they must come after the input and output directory paths.All OptionsTo see all available commands and the full list of plottable curves, use the --help flag.python batch_chromatogram_plotter.py --help
The output will be:usage: batch_chromatogram_plotter.py [-h] [--curves CURVES [CURVES ...]] [--xlim MIN MAX] [--ylim MIN MAX] input_dir output_dir

Batch process ÄKTA .zip result files (including modern UNICORN 6 format) and export plots.

positional arguments:
  input_dir             Path to the folder containing your .zip result files.
  output_dir            Path to the folder where plots will be saved.

options:
  -h, --help            show this help message and exit
  --curves CURVES [CURVES ...]
                        A list of specific curve names to plot. Use quotes for names with spaces.
                        If not provided, plots UV, Conductivity, and Gradient by default.

                        Available curves can include:
                        - Fractions
                        - Injection
                        - "Run Log"
                        - "UV 1_280"
                        - "UV 2_295"
                        - "UV 3_0"
                        - Cond
                        - "% Cond"
                        - "Conc B"
                        - "System flow"
                        - "System linear flow"
                        - "PreC pressure"
                        - "DeltaC pressure"
                        - "Sample flow"
                        - "Sample linear flow"
                        - "Sample pressure"
                        - pH
                        - "System pressure"
                        - "PostC pressure"
                        - "Cond temp"
                        - "xUV cell path length"
                        - "Sample flow (CV/h)"
                        - "System flow (CV/h)"

  --xlim MIN MAX        Set the manual limits for the X-axis (Volume).
  --ylim MIN MAX        Set the manual limits for the primary Y-axis (the first curve plotted).
LicenseThis project is licensed under the terms of the GPLv2 license. See the LICENSE file for details.
