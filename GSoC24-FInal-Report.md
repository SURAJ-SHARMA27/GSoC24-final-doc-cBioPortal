# Final Evaluation Report for GSoC 2024

<div align="center">
<img src="https://github.com/user-attachments/assets/b276b3c0-9797-413e-abea-d6f162cd5661" alt="drawing" width="500"/>

</div> 



## Details

|  |  |
| --- | --- |
| Name | [Suraj Sharma](https://www.linkedin.com/in/suraj-sharma-239894223/)(<img src="https://user-images.githubusercontent.com/48355572/263745495-93ca876f-c21d-4af3-aa8e-e164cdc46b92.png" width="14.5px" height="14px">[@SURAJ-SHARMA27](https://github.com/SURAJ-SHARMA27)) |
| Organisation | [cBioPortal](https://www.home.cern/) |
| Mentor | [Zeynep Karagöz](https://www.linkedin.com/in/zeynepkaragoz/)(<img src="https://user-images.githubusercontent.com/48355572/263745495-93ca876f-c21d-4af3-aa8e-e164cdc46b92.png" width="14.5px" height="14px">[@zeynepkaragoz](https://github.com/zeynepkaragoz)), [Sowmiyaa Kumar](https://www.linkedin.com/in/sowmiyaa-senthil-kumar-61a29b121/)(<img src="https://user-images.githubusercontent.com/48355572/263745495-93ca876f-c21d-4af3-aa8e-e164cdc46b92.png" width="14.5px" height="14px">[@sowmiyaa-kumar](https://github.com/sowmiyaa-kumar)), [Anika Bongaarts](https://www.linkedin.com/in/anikabongaarts/) |
| Project | [Frontend visualization and incorporation of single cell data in cBioPortal](https://summerofcode.withgoogle.com/media/user/29844e671937/proposal/gAAAAABmwsVC6UePXC5jCXcrCtOY-FUx12fwsDM1mhnwSQrSO9iXUdYuQ-p3r0yXDGTDGK29-FKcueOHdMXUwSTa2aqqbxmf3AA-6YoTLJK9eOWp4p2nfYU=.pdf) |


## About Project

This project aims to address the gap by developing a dedicated single-cell analysis
module within cBioPortal, focusing specifically on the MSK Spectrum dataset (genomic
and single cell gene expression data stored in two different platforms).  <img src="https://user-images.githubusercontent.com/48355572/263672801-5929885f-9227-4be3-a686-ea3fbeff13d2.gif" width="12.5px" height="12.5px">

> **Background**: Researchers often struggle to integrate single-cell gene expression data analysis with
existing cancer genomics workflows. cBioPortal, a valuable resource for bulk genomics
analysis, lacks support for single-cell gene expression data visualization. This hinders
researchers from leveraging both data types for a more comprehensive understanding
of cancer biology.

<br/>

## Project Report

> A new tab within cBioPortal will be specifically designed for single-cell data exploration
in the study view.

### 💡 Single Cell Tab

**Conditional Rendering:** This tab is displayed only when:
- This tab is available on the Study View.
- A user is searching for an individual study.
- The study contains `genericAssaysProfiles` (data of type generic assay).

**Reason for Conditional Rendering:**
- Ensures the tab is only shown when relevant single cell data is available.
- Enhances user experience by providing targeted and meaningful data visualization.

<div align="center">
<img src="https://github.com/user-attachments/assets/195dcea2-5dd2-4914-94e2-ac05690d38e5" alt="drawing" width="1000"/>

</div> 

<br/>
<br/>

### 📊 Chart Configuration Panel in Single Cell Tab

**Purpose:**  
Provides an interactive interface for users to configure the visualization of single cell data.

**User Interaction:**

- **Initial State:** Contains a single dropdown, "Select a single cell profile," populated based on the searched `studyId`.
  
- **Dynamic Configuration:**
  1. **Step 1:** User selects a molecular profile.
  2. **Step 2:** A second dropdown appears, "Select Type of Chart," with options: Stacked Bar, Histogram, Pie Chart.
  
- **Chart-Specific Options:**  
  Upon chart type selection, the panel dynamically enables relevant configuration options tailored to the selected visualization type.


<br/> 

### 📈 Stacked Bar Chart Configuration

**Sort By:**
- Upon selecting "Stacked Bar" from the chart type dropdown, a third dropdown appears: "Sort By".
- **Options:** Cell Type/Phase.
- **Sorting:** The selected cell fraction appears first in each bar in ascending order.
- **Reverse Sorting:** A toggle button allows reversing the sorting order.

**Graph Customization:**

- **Resize Graph:**
  - A toggle button to enable dynamic width/height adjustment.
  - A throttle for resizing appears in the chart configuration panel for user customization.

- **Toggle Axes:**
  - A toggle button to swap the chart axes.

- **Sample IDs Dropdown:**
  - A separate dropdown containing all sample IDs.
  - Allows selection of single or multiple sample IDs.
  - The stacked bar chart updates to show data for the selected sample IDs.

**Dynamic Tooltip:**
- Displays cell type values, names, and colors upon hovering over each bar.
- Includes the sample ID as a heading.
- Clicking on the sample ID redirects to the patient summary page for that sample.

**Download Options:**
- A download icon that shows three options upon hovering: PDF, SVG, DATA.
- Allows downloading the graph in the selected format.


<div align="center">
<img src="https://github.com/user-attachments/assets/9db61c43-fb13-4bf5-9385-fedf66bd02a7" alt="drawing" width="1000"/>

</div> 
<br/><br/>

### 🥧 Pie Chart Configuration

- Upon selecting "Pie Chart" from the chart type dropdown, the pie chart is generated for the selected molecular profile.

**Composition Visualization:**
- Displays the composition of cell types for the selected molecular profile.

**Tooltip Table:**
- Shows the percentage of each cell with its name and color.
- The tooltip row is highlighted when hovering over a particular cell type in the pie chart.
- **Toggle Button:** Makes the tooltip stationary upon clicking, preventing it from vanishing on mouse out events.

**Download Options:**
- A download icon that shows three options upon hovering: PDF, SVG, DATA.

<div align="center">
<img src="https://github.com/user-attachments/assets/8933cafa-30f2-4c64-9619-5abdf5c7c301" alt="drawing" width="1000"/>

</div> 

<br/><br/>

### 📊 Histogram Configuration

- Upon selecting "Histogram" from the chart type dropdown, an additional dropdown appears.

**Cell Type/Fraction Selection:**
- User selects a cell type/fraction from this dropdown.

**Data Handling:**

- **Data Bins:**
  - Resolves databins promises based on the selected cell type/fraction.
  - The bar chart is plotted after retrieving the databins.

- **Custom Data Bins:**
  - Functionality for adding custom databins.
  - Corresponding points are fetched for the entered custom databin range and plotted on the chart.

**Download Options:**
- A download icon that shows three options upon hovering: PDF, SVG, DATA.
- Allows downloading the graph in the selected format.

<div align="center">
<img src="https://github.com/user-attachments/assets/99f3b721-cb55-4a90-a364-0ccc86580748" alt="drawing" width="1000"/>

</div> 

<br/><br/>

### 🧬 Gene Expression

- When "Gene Expression" is selected from the first dropdown, the chart type dropdown is auto-populated with "Box Plot."

**Gene Selection:**
- A dropdown appears for selecting a gene, displaying all available genes.
- After selecting a gene, a scattered box plot is plotted.

**X-Axis:**
- Displays all the cells.

**Hover Interaction:**
- Displays the composition of sample ID, tissue, and corresponding value for each dot.

**Color Options:**

- **Default Color:** All dots are colored the same by default.
- **Color by Tissue:** Dots representing the same tissue are colored the same.
- **Color by Sample ID:** Dots representing the same sample ID are colored the same.

<div align="center">
<img src="https://github.com/user-attachments/assets/56a0ab56-4a14-43cc-9f39-28ff8319d08c" alt="drawing" width="1000"/>

</div> 

<br/>

## Contributions <img src="https://user-images.githubusercontent.com/48355572/263670717-89cefc3e-346f-4b89-9f3a-36d7f14bb25c.png" width="18.5px" height="20px">

I have made multiple commits spread across the subsequent Pull Requests and are listed below:


- [x] Add Stacked Bar Chart and sorting to Plots Tab  ([**PR #4960**](https://github.com/cBioPortal/cbioportal-frontend/pull/4960)) 🟨


Implemented a new feature allowing users to sort by minorCategory.
- Added a dropdown menu with minorCategory options for sorting.
- Sorted Stacks by Selected MinorCategory:

For the selected option from the dropdown, entities will appear at the beginning of each stack in a sorted order with respect to the count of chosen minorCategory.

<br/>

- [x] Scattered-Box-plot added ([**PR #4948**](https://github.com/cBioPortal/cbioportal-frontend/pull/4948)) 🟨

Added scattered box plot in which VictoryStack and VictoryBoxPlot are used.
- The logic processes a nested JSON structure to transform the data into a structured format (transformedData). It ensures each gene entry has associated color and stroke color attributes, reuses existing colors where possible, and assigns new colors from predefined palettes where necessary. The result is stored in the component's state.
For each gene name, a tuple object is created containing:
The gene value.
- The cell type name (cellname).
- The tissue name (tissuename).
- The sample key as parentId.
- Placeholders for various colors (color, bwColor, bwStrokeColor, strokeColor, tissueColor, tissueStrokeColor).

<br/>

- [x] Gsoc 2024 single cell tab- stackedBar,piechart and bar plots added ([**PR #4921**](https://github.com/cBioPortal/cbioportal-frontend/pull/4921)) 🟨

In this pull request stacked bar , piechart and bar plot components have been added for single cell tab along with custom tooltips and downloading options.


<br/>

### 🛠️ Challenges Faced During GSoC Project

One of the tasks that required extra time and attention was adding a customized tooltip for the stacked bar and pie chart. The task required a deep dive into the VictoryCharts documentation, as I had to override the default interaction events and implement custom events to achieve the desired functionality. This involved making the tooltip dynamic and responsive to various states. I also had to manage the tooltip's visibility and positioning based on the user's interactions with the chart.

<br/>

### 🎓 Takeaways from My GSoC Experience

The most valuable lesson I gained from this project was the importance of time management. Balancing my GSoC responsibilities while working at another company was particularly challenging, especially during critical phases. However, I managed to align my work with the client project while making significant progress on GSoC tasks. This experience taught me how to effectively prioritize and manage my time, a skill that will undoubtedly benefit me in future endeavors.

On the technical side, my understanding of frontend visualization, particularly with diverse datasets, has deepened significantly. I became proficient in using the VictoryCharts library, which was pivotal in implementing single cell visualizations. Additionally, I honed my skills with MobX for state management.

<br/>

### 📝 Blogs

I have written some blogs midway through this journey. You can enjoy them here:

- [My GSoC Journey with cBioPortal Community: Bonding and First Week of Coding](https://medium.com/@surajrace21/my-gsoc-journey-with-cbioportal-community-bonding-and-first-week-of-coding-647537d4ae94)
- [Week Two of My Google Summer of Code (GSoC) Journey with cBioPortal](https://medium.com/@surajrace21/week-two-of-my-google-summer-of-code-gsoc-journey-with-cbioportal-99fa2478d3db)

<br/>

## Summary

Participating in **Google Summer of Code** (GSoC) for the very first time was a full learning experience for me. I'm immensely grateful to my mentors, [@zeynepkaragoz](https://github.com/zeynepkaragoz), [@sowmiyaa-kumar](https://github.com/sowmiyaa-kumar), and [Anika Bongaarts](https://www.linkedin.com/in/anikabongaarts/) , for this opportunity. I am thankful for their invaluable guidance, feedback, and understanding throughout the project. They have been very supportive throughout the project.

> Special Thanks to  [Tim Kuijpers](https://www.linkedin.com/in/kuijperstim/) and [Joris Louwen](https://www.linkedin.com/in/joris-louwen/) for providing immense support and help throughout the program.

**Thanks and Regards,**

**Suraj Sharma**
