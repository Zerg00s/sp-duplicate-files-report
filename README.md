# Power BI Report for finding large duplicate files in SharePoint Online

SharePoint sites can quickly become cluttered with duplicate files, taking up valuable storage space and making it difficult to find the information you need.

To help solve this problem, I've created a re-usable Power BI report that searches for duplicates within a single SharePoint site. This report makes it easy to identify and delete unnecessary duplicates, saving you both time and storage space.

## Download the PBIX Report file
[➡️ Download the Duplicate Files.pbix report from here ⬅️](https://github.com/Zerg00s/sp-duplicate-files-report/raw/main/Duplicate%20Files.pbix)




![image](https://user-images.githubusercontent.com/2797648/217652660-bd7c86a4-c49e-4f84-a7c6-a07909e0bf4b.png)

## Getting Started

To get started, you'll need to download the [.pbix report file](https://github.com/Zerg00s/sp-duplicate-files-report/raw/main/Duplicate%20Files.pbix). Once the file is downloaded, you'll be able to open it in Power BI and update a target SharePoint site.

- Double click on the downloaded .pbix file to open it
- Click on Transform Data
- Then click on Source and update the site URL to point to a site of your choice
- Click on Close an Apply.

![image](https://user-images.githubusercontent.com/2797648/217654290-1fcbc714-614e-4888-b0f5-b8b201931a28.png)

- Sign in with your Microsoft account when asked.
- Click on Refresh to refresh the data. 
- Publish the report to a workspace of your choice.

Once the report is published, you'll be able to use the filters provided to search for duplicates by file size and number of duplicates found. You can also view a table of all files, including the file name, size, and full path.

With this report, managing large duplicate files in SharePoint sites has never been easier. Give it a try and see for yourself how much time and storage space you can save.


## Getting Started - Multiple sites
The "Duplicate Files - Multiple Sites" report in Power BI is designed to provide insights into file data across multiple SharePoint sites. This tutorial will guide you on how to set up 2 or 3 SharePoint sites within the report to aggregate and analyze file data.

###  [➡️ Download the Duplicate Files - Multiple sites.pbix report from here ⬅️](https://github.com/Zerg00s/sp-duplicate-files-report/raw/main/Duplicate%20Files%20-%20Multiple%20sites.pbix)
- Open the report in Power BI Desktop

### Access Power Query Editor

- Once the report is open, go to the "Home" tab in Power BI Desktop.
- Click on "Transform Data" to open the Power Query Editor.

### Update Site URLs in Existing Queries
- In the Queries pane on the left, click on Site_Files-1 to select it.
- In the formula bar at the top, locate the SharePoint site URL and replace it with the correct URL for the first site.
  - For example, replace "https://cleverpointlab.sharepoint.com" with "https://cleverpointlab.sharepoint.com/sites/YourSite1".
- Repeat the above two sub-steps for Site_Files-2 and Site_Files-3, replacing the SharePoint site URLs with the correct URLs for the second and third sites respectively.

### Updating All_Files Query

1. Access Power Query Editor:

- Open your report in Power BI Desktop.
- Go to the Home tab and click on Transform Data to access the Power Query Editor.

2. Navigate to the "All_Files" Query:

- In the Queries pane on the left, click on the All_Files query to select it.

3. Access Advanced Editor:

- Within the Power Query Editor, go to the Home tab.
- Click on Advanced Editor.

4. Update M Code:

- Replace the existing M code in the Advanced Editor with the modified script provided above, depending on whether you have two or four sites. For example;


```
let
    Query1 = #"Site_Files-1",
    Query2 = #"Site_Files-2",
    Query3 = #"Site_Files-3",
    Query4 = #"Site_Files-4",
    AppendedQuery = Table.Combine({Query1, Query2, Query3, Query4})
in
    AppendedQuery

```
- Click "Done" to close the Advanced Editor.

5. Apply Changes:

- Click Close & Apply to apply the changes and return to the main Power BI interface.

### For Two Sites:
If you have two sites, you'll only need to include Site_Files-1 and Site_Files-2 in the Table.Combine function. Here’s how you would modify the script:

```
let
    Query1 = #"Site_Files-1",
    Query2 = #"Site_Files-2",
    AppendedQuery = Table.Combine({Query1, Query2})
in
    AppendedQuery

```

### For Four Sites:
If you have four sites, you would need to create or update a query for the fourth site (e.g., Site_Files-4), and then include it in the Table.Combine function. Here's how you would modify the script:

```
let
    Query1 = #"Site_Files-1",
    Query2 = #"Site_Files-2",
    Query3 = #"Site_Files-3",
    Query4 = #"Site_Files-4",
    AppendedQuery = Table.Combine({Query1, Query2, Query3, Query4})
in
    AppendedQuery

```

Sometimes Power BI creates unnecessary relationships between data, and this can cause the following error:
![image](https://github.com/Zerg00s/sp-duplicate-files-report/assets/2797648/6b64a462-a93d-4d21-af54-bfba23634fc4)


To fix this you need to go to model view and delete all existing relationships 

![image](https://github.com/Zerg00s/sp-duplicate-files-report/assets/2797648/254dcd95-8137-4379-b1ff-5598399f7684)

![image](https://github.com/Zerg00s/sp-duplicate-files-report/assets/2797648/b120d0db-0b26-4100-9331-1b9e97b4d401)



Happy reporting!
