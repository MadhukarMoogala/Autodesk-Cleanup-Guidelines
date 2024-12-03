### Managing Temporary and Auxiliary Files in Autodesk Applications

Autodesk products generate various temporary and auxiliary files during their operation. While most of these files are removed after the application session ends, some persist and can be safely deleted under certain conditions. Below is a detailed guide for handling these files.

---

### **Deleting Temporary Files**

To delete general temporary files:

1. Follow the steps in the Autodesk article on [how to delete temporary files in Windows](https://www.autodesk.com/support/technical/article/caas/sfdcarticles/sfdcarticles/How-to-delete-temporary-files-in-Windows.html).
2. Temporary files are typically found in these directories:
   - `%temp%`
   - `%localappdata%\Autodesk`

Deleting temporary files here will cover most Autodesk products. However, be cautious of auxiliary files that might impact performance if removed.

---

### **Auxiliary Files: To Delete or Not to Delete?**

Auxiliary files are created by Autodesk products to enhance functionality and performance. While these files can often be deleted, doing so may have consequences.

#### **AutoCAD Auxiliary Files**

1. **GraphicsCache**
   
   - **Location**: `%localappdata%\Autodesk`
   
   - **Example Command to Locate**:
     
     ```batch
     set TargetFolder=%localappdata%\Autodesk
     dir /ad /b /s "%TargetFolder%\GraphicsCache"
     
     ```
   
   - **Impact of Deletion**:
     Deleting `GraphicsCache` will force AutoCAD to regenerate the cache during subsequent sessions, which may lead to slower performance when reopening CAD files.  
     **Recommendation**: Only delete if you need to reclaim significant disk space and can tolerate the regeneration time.

2. **RecentBlocks**
   
   - **Location**: `%appdata%\Autodesk`
   
   - **System Variable**: `BLOCKSRECENTFOLDER`
   
   - **Example Command to Locate**:
     
     ```batch
     set TargetFolder=%appdata%\Autodesk
     dir /ad /b /s "%TargetFolder%\RecentBlocks"
     
     ```
   
   - **Impact of Deletion**:
     Cleaning this folder removes the list of recently used blocks but does not harm AutoCAD's core functionality.  
     **Recommendation**: Safe to delete if users no longer need the history.

3. **ActivityInsights**
   
   - **Location**: `%localappdata%\Autodesk`
   - **System Variable**: `ACTIVITYINSIGHTSPATH`
   - **Impact of Deletion**:
     Deleting this folder will remove activity logs and analytics files.  
     **Recommendation**: Safe to delete if activity tracking data is not required.



#### **AutoCAD Map 3D Cache Files**

- For instructions specific to AutoCAD Map 3D, refer to [this Autodesk article](https://www.autodesk.com/support/technical/article/caas/sfdcarticles/sfdcarticles/Deleting-AutoCAD-Map-3D-cache-files.html).

---

#### **Revit Temporary Files**

- Revit also generates temporary files during operation. Guidance for cleaning these files is available [here](https://lazybim.com/cleanup-revit-temp-files/).
