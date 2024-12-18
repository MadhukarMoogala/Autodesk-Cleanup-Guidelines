# Managing Temporary and Auxiliary Files in Autodesk Applications

Autodesk products generate various temporary and auxiliary files during their operation. While most of these files are removed after the application session ends, some persist and can be safely deleted under certain conditions. Below is a detailed guide for handling these files.

---

## ⚠️ **Important Note**

> ⚠️ **Do not remove any of these files while the Autodesk product is running.**

---

## 🗂️ **Deleting Temporary Files**

To delete general temporary files:

1. Follow the steps in the Autodesk article on [how to delete temporary files in Windows](https://www.autodesk.com/support/technical/article/caas/sfdcarticles/sfdcarticles/How-to-delete-temporary-files-in-Windows.html).
2. Temporary files are typically found in these directories:
   - `%temp%`
   - `%localappdata%\Autodesk`

Deleting temporary files here will cover most Autodesk products. However, be cautious of auxiliary files that might impact performance if removed.

---

## 🧩 **Auxiliary Files: To Delete or Not to Delete?**

Auxiliary files are created by Autodesk products to enhance functionality and performance. While these files can often be deleted, doing so may have consequences.

### 🔧 **AutoCAD Auxiliary Files**

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
   
   - **Location**: `%localappdata%\Autodesk\ActivityInsights`  
   - **System Variable**: `ACTIVITYINSIGHTSPATH`  
   - **Impact of Deletion**:  
     Deleting this folder will remove activity logs and analytics files.  
     **Recommendation**: Safe to delete if activity tracking data is not required.

4. **Design Center `.cdc` Files**  
   
   - **Location**: Adjacent to the `.dwg` files in the same folder.  
   - **Impact of Deletion**:  
     Deleting `.cdc` files will remove the cached thumbnails. This will not affect the drawings themselves, but thumbnails will need to be regenerated the next time the folder is browsed in Design Center, potentially causing a delay.  
     **Recommendation**: Safe to delete if thumbnail caching is not required or if you need to free up space.

---

## 📄 **Common AutoCAD Extension Files**

AutoCAD uses a variety of file extensions to manage drawing data, customization, configuration, and temporary operations. Below is an overview of some common file types:

### 🖼️ **Drawing Files**

- **`.dwg`**  
  
  - **Purpose**: Primary drawing file format. Stores all design data for a project.  
  - **Recommendation**: Backup regularly; do not delete unless explicitly unnecessary.

- **`.bak`**  
  
  - **Purpose**: Backup of the `.dwg` file created during save operations.  
  - **Recommendation**: Safe to delete if the primary `.dwg` file is verified and intact.

### 🛠️ **Custom Configuration Files**

- **`.dwt`**  
  
  - **Purpose**: Drawing template file. Used for creating new drawings with predefined settings.  
  - **Recommendation**: Retain as required for consistent project standards.

- **`.pc3`**  
  
  - **Purpose**: Plot configuration file. Stores settings for plotting and printers.  
  - **Recommendation**: Keep for projects using specific printing configurations.

- **`.ctb` / `.stb`**  
  
  - **Purpose**: Plot style table files. Control line weights and colors during plotting.  
  - **Recommendation**: Retain as needed for accurate plotting.

- **`.arg`**  
  
  - **Purpose**: AutoCAD profile settings. Stores user preferences for tool palettes, menus, etc.  
  - **Recommendation**: Backup important profiles; safe to delete unused files.

---

## 🧳 **Customization and Extensions**

- **`.cui` / `.cuix`**  
  
  - **Purpose**: Custom user interface files for menus, ribbons, and toolbars.  
  - **Recommendation**: Retain important customizations; backup regularly.

- **`.lsp`**  
  
  - **Purpose**: Lisp script files used for automation and customization.  
  - **Recommendation**: Useful for custom workflows; retain as needed.

- **`.arx`**  
  
  - **Purpose**: AutoCAD Runtime Extension files. Extend AutoCAD functionality with custom applications.  
  - **Recommendation**: Only delete if no longer required.

---

## 💾 **Support Files**

- **`.shx`**  
  
  - **Purpose**: Shape and font files used for text and annotations.  
  - **Recommendation**: Retain required fonts; missing `.shx` files can cause display issues.

- **`.pat`**  
  
  - **Purpose**: Hatch pattern files.  
  - **Recommendation**: Retain project-specific patterns; unused ones can be removed.

- **`.lin`**  
  
  - **Purpose**: Linetype definition files.  
  - **Recommendation**: Retain linetypes in active use; unused files can be removed.

---

## 🔄 **Recovery and Temporary Files**

### 🔐 **`.dwl` and `.dwl2` Files**

- **Purpose**: Used by the WHOHAS feature to manage file locks and track file access.  
- **Location**: Created in the same directory as the `.dwg` files being accessed.  
- **Impact of Deletion**: Safe to remove when the associated drawing files are closed. These files are automatically generated when the drawing is reopened.

---

### 📝 **`.ac$` and `.sv$` Files**

- **Purpose**:
  - `.ac$`: Temporary files used by the SAVE command and other operations.
  - `.sv$`: Autosave files created as part of the autosave feature for recovery purposes.
- **Location**: Typically found in the temporary file directory specified in AutoCAD's options.
- **Impact of Deletion**:  
  - Deleting `.ac$` files during an active session may cause data loss for unsaved changes.  
  - Deleting `.sv$` files will remove autosave data, which might be needed for recovery after a crash.  
- **Recommendation**:  
  - **`.ac$`**: Do not delete while AutoCAD is running.  
  - **`.sv$`**: Safe to delete after confirming no unsaved data is required.

---

## 🔄 **Data Exchange Files**

- **`.dxf`**  
  
  - **Purpose**: Drawing Exchange Format. Used for sharing data between different CAD applications.  
  - **Recommendation**: Retain for interoperability; backup critical data.

- **`.xml`**  
  
  - **Purpose**: Extensible Markup Language files used for certain configuration and data exchange purposes.  
  - **Recommendation**: Retain as necessary for application-specific configurations.

---

## 🌍 **AutoCAD Map 3D Cache Files**

- For instructions specific to AutoCAD Map 3D, refer to [this Autodesk article](https://www.autodesk.com/support/technical/article/caas/sfdcarticles/sfdcarticles/Deleting-AutoCAD-Map-3D-cache-files.html).

---

## 🏗️ **Revit Temporary Files**

- Revit also generates temporary files during operation. Guidance for cleaning these files is available [here](https://lazybim.com/cleanup-revit-temp-files/).

---

### **Contribution Guidelines**

Thank you for your interest in contributing to this repository! Follow these guidelines to ensure a smooth and productive collaboration:

---

#### **Code of Conduct**

- Be respectful and inclusive.
- Avoid submitting harmful or misleading suggestions.
- Constructive feedback is always welcome.

---

#### **What We’re Looking For**

You can contribute in the following ways:

1. **New Insights**: Document other temporary or auxiliary files generated by Autodesk applications not currently listed.
2. **Best Practices**: Share workflows for handling these files in specific scenarios.
3. **Scripts**: Provide sample scripts (batch files, PowerShell, Python, etc.) for automating file cleanup processes.
   - Scripts should focus on guidance, not automation for running applications.
   - Include detailed comments in the scripts to explain their behavior.
4. **Errors and Omissions**: Suggest corrections or updates for the documentation.
5. **Platform-Specific Guidance**: Add instructions for handling files on non-Windows platforms, if applicable.
6. **Performance Optimization Tips**: Share tips to manage these files without negatively impacting system performance or application behavior.

---

#### **What We’re NOT Looking For**

- **Automated Cleanup Tools**: This repository is intended for guidance, not providing ready-made tools for file deletion.
- **Irrelevant Contributions**: Avoid non-Autodesk-related topics or unrelated temporary file management techniques.
- **Harmful Practices**: Any suggestions that could disrupt workflows or cause data loss will not be accepted.

---

#### **How to Contribute**

1. **Fork the Repository**: Create a personal copy of this repository on GitHub.
2. **Create a Feature Branch**: Work on your changes in a dedicated branch.
   - Example: `git checkout -b feature/add-revit-temp-files`
3. **Test Your Changes**: If adding scripts, test them in a controlled environment.
4. **Submit a Pull Request (PR)**:
   - Provide a clear description of the changes.
   - Reference any related issues or discussions.
   - Include usage examples and explain any potential risks.
5. **Address Feedback**: Respond promptly to comments on your PR.

---

#### **Documentation Standards**

- Use clear and concise language.
- Adhere to Markdown formatting for consistency.
- Include file locations, potential impacts, and recommendations for each file type.
- If suggesting scripts, follow these conventions:
  - **Cross-Platform Compatibility**: Ensure scripts work on common environments or specify limitations.
  - **Non-Destructive Testing**: Include options to simulate file deletion before executing.
  - **Error Handling**: Add safeguards to prevent accidental deletions.

---

#### **Example Submission**

When contributing, format your additions as follows:

**Section Title**: Briefly describe the type of file or functionality (e.g., *AutoCAD `GraphicsCache`*).

1. **Location**: Specify the folder(s) where the file is commonly found.
2. **Impact of Deletion**: Explain the consequences of deleting the file.
3. **Example Command (Optional)**: Provide sample code to identify or manage the files.
4. **Recommendation**: Indicate whether it is safe to delete and under what circumstances.

---

#### **Feedback and Questions**

If you have any questions about contributing, feel free to:

- Open an issue in the repository.
- Email the repository maintainers.
