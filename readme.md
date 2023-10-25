# PHP String Finder in WordPress

PHP String Finder is a powerful utility plugin for WordPress, enabling developers and administrators to conveniently search for specific strings within the PHP files of their WordPress environments. This tool is invaluable for various scenarios including debugging, conducting code reviews, and auditing the use of functions or API calls across themes or plugins.

## Table of Contents

- [Main Features](#main-features)
- [Installation](#installation)
- [Usage Guide](#usage-guide)
- [Limitations](#limitations)
- [Contribution](#contribution)
- [Author Information](#author-information)
- [License](#license)

## Main Features

- **User-friendly Interface:** Seamlessly integrates with the WordPress admin dashboard.
- **Comprehensive Search:** Scours through all PHP files in your WordPress directory, including all subdirectories.
- **Optimized for Performance:** Efficiently handles large file structures by ignoring files larger than a specific threshold.
- **Security-Conscious:** Implements nonce checks to validate the authenticity of search requests, protecting against cross-site request forgery (CSRF).
- **Customizable Execution Time:** Prevents script timeouts during extensive searches by allowing customization of script execution time.

## Installation

1. Download the PHP String Finder plugin's ZIP file.
2. Log into your WordPress admin dashboard.
3. Navigate to "Plugins" > "Add New".
4. Click "Upload Plugin" and select the downloaded ZIP file.
5. Click "Install Now".
6. After installation, click "Activate" to start using the plugin.

Post-activation, the PHP String Finder plugin is accessible from the WordPress admin dashboard within the "Tools" menu.

## Usage Guide

1. From your WordPress admin, go to "Tools" > "PHP String Finder".
2. A form with a text input field is presented on this page.
3. Input the string you are looking to find within your PHP files.
4. Hit the "Search" button to initiate the process.
5. Search results, including the file paths, will be listed on the page for all PHP files containing the specified string.

## Limitations

- **File Size Constraints:** Files exceeding a certain size (default: 500,000 bytes) are excluded from searches to avoid high memory consumption and potential PHP timeouts. This means larger PHP files might not be searched.
- **Execution Time:** By default, the plugin operates with a 600-second (10-minute) execution time limit. Depending on the number of files, some searches might be incomplete due to this restriction.
- **Error Handling:** The plugin encompasses basic error handling for exceptions but might not intercept all possible errors, especially those occurring at the server level.
- **Search Precision:** Current search functionality is confined to exact string matches and does not support regex or partial match searches.
- **Server Load Considerations:** Intensive file searches may impose a significant load on server resources. It's advisable to run extensive searches during low-traffic periods.
- **File System Permissions:** Depending on server configurations, the plugin may encounter restrictions reading certain directories or files due to file system permissions.

## Contribution

Developers are welcome to enhance the features of the PHP String Finder plugin by contributing to its source code. Parameters such as `$maxFileSize` and script execution time can be adjusted to suit specific project requirements or hosting environments.

## Author Information

- **D.Kandekore**

For inquiries, suggestions, or issues relating to the plugin, please reach out to the author.

## License

PHP String Finder is licensed under GPL-2.0.
