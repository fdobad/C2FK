# Using Visual Studio to compile Cell2Fire for windows  

Tested on Microsoft Visual Studio Community 2022 (64-bit) - Version 17.6.5

## Preparation  

Get Visual Studio (Community), install Visual C++ Workflow  

Get these libraries (download & un7zip them):  

- dirent-1.23.2 : https://github.com/tronkko/dirent/releases  
- boost 1.81.0 : https://boostorg.jfrog.io/artifactory/main/release/1.81.0/source/  
- eigen 3.4.0 : https://gitlab.com/libeigen/eigen/-/releases  

## Setup the solution project  

0. If not found repo/Cell2FireC/Cell2fire.sln:  

	- Menu > File > New > Project from existing code  
	- Type : Visual C++  
	- Project file location: Cell2FireC  
	- Project name: Cell2Fire  

Open Cell2Fire.sln that should placed be next to .h and .cpp files  

1. MenuBar : Project > Properties
2. ComboBox : Configuration : Release (then repeat with Debug)
3. Configuration Properties  

	- General > Target Name : `$(ProjectName)`  
	- C/C++ > AdditionalIncludeDirectories : `C:\dev\dirent-1.23.2\include;C:\dev\boost_1_81_0\;C:\dev\eigen-3.4.0`  
	- C/C++ > Preprocessor > PreprocessorDefinitions : `_USE_MATH_DEFINES`  
	- Debugging > Command Arguments : `--input-instance-folder C:/...repos/C2FSB/data/Hom_Fuel_101_40x40/ --output-folder C:/.../results/`  
    - Linker > System > Subsystem : Console (/SUBSYSTEM:CONSOLE)

Replace directories as needed  

## Compile  
### Debug
1. Press play on "Local Windows Debugger", and correct mistakes until you see a command window with:  
```
------ Command line values ------
InFolder: C:\Users\ferna\source\fire2a\C2FSB\data\Hom_Fuel_101_40x40\
OutFolder: C:\Users\ferna\source\fire2a\C2FSB\data\Hom_Fuel_101_40x40\results
------------------Forest Data ----------------------

Forest DataFrame from instance C:\Users\ferna\source\fire2a\C2FSB\data\Hom_Fuel_101_40x40\Data.csv
Number of cells: 1600
```  

### Build Release 

2.1. Change Debug to Release (two comboboxes to the left)  
2.2. MenuBar : Build > Configuration Manager  
		- Project contexts (check the project configuration to build or deploy)  
		- Configuration : Debug  
		- Close  
2.3. MenuBar : Build > Clean Solution  
2.3. MenuBar : Build > Build Solution  

# sample run

windows cmd

    > cd C2FK
    > python main.py --input-instance-folder data\Homogeneous --output-folder data\Homogeneous\results --grids --final-grid --verbose

Alternative for activating virtual environment

    # Install QGIS
    > winget install --id OSGeo.QGIS
    Install fire2am plugin
    call C:\OSGeo4W\bin\o4w_env.bat
