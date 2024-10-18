# Carbon-Star-Analysis
Radio Spectroscopical analysis of Carbon Stars [CIT6](https://en.wikipedia.org/wiki/CIT_6) and [CW Leonis](https://en.wikipedia.org/wiki/CW_Leonis) 

## Table of Contents
- [Features](#Features)
- [Installation](#installation)
- [Usage](#usage)
- [Data Processing](#data-processing)
- [Peak Detection and Classification](#peak-detection-and-classification)
- [Smoothing and Gaussian Fitting](#smoothing-and-gaussian-fitting)
- [Visualization](#visualization)
- [Contributing](#contributing)
- [License](#license)


## Features

This project offers a range of tools for analyzing and visualizing radio spectroscopic data, with the following features:

- **Peak Detection and Classification**: Automatically detects peaks in the spectroscopic data and classifies them by matching the detected peaks with known molecular transitions.

- **Smoothing Spectral Data**: Applies a Savitzky-Golay filter to smooth the Tant data for both CIT6 and IRC+10216, helping to reduce noise and improve clarity in peak detection.

- **Gaussian Fitting**: Fits a Gaussian model to zoomed-in sections of CIT6 spectral data, allowing precise modeling of spectral lines and better visualization of the line profiles.

- **Dual-Dataset Comparisons**: Provides tools to compare and visualize spectral data from both CIT6 and IRC+10216, plotting the data side by side for easy comparison.

- **Annotation and Visualization**: Annotates detected peaks with molecular names in the plots, making it easy to identify the molecules responsible for each spectral line. Both the original and smoothed data can be plotted for CIT6 and IRC+10216.

- **Data Handling and Export**: Processes multiple spectroscopic data files and outputs the results in easy-to-read `pandas` DataFrames, including peak frequencies, associated molecules, and integrated intensities (Tint).


### Installation 

To use the code within this repository you will need to install the following libraries:

```python
!pip install numpy pandas matplotlib astropy scipy specutils
```

If you're running the code in Google Colab, you can mount Google Drive using:
 ```python
from google.colab import drive
drive.mount('/content/drive/')
%cd /content/drive/MyDrive
```


## Usage

Load the spectral line data for both CIT6 and CW Leonis:
```python
molecule_data = pd.read_excel('detectedline_table.xlsx', sheet_name='CIT6')
molecule_data['Rest Frequency'] = molecule_data['Rest Frequency'].astype(float) / 1000.  # Convert MHz to GHz
```

## Data Processing

The spectral data is loaded using pandas.read_csv and concatenated for further analysis:
```python
pathlist = sorted(Path('data/Apr3/CIT6Apr3/').glob('*.txt'))
cit_spec = pd.DataFrame()
for path in pathlist:
    ind_spec = pd.read_csv(path, sep='\s+', names=['order', 'freq', 'Tant'])
    cit_spec = pd.concat([cit_spec, ind_spec])
cit_spec = cit_spec.sort_values(by='freq')
```


## Peak Detection and Classification

## Smoothing and Gaussian Fitting

## Visualization

## Contributing

## License
