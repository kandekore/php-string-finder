<?php
/**
 * Plugin Name: PHP String Finder in WordPress
 * Description: A plugin to search for a string within PHP files.
 * Version: 1.0
 * Author: D.Kandekore
 */

// Prevent direct file access
if (!defined('ABSPATH')) {
    exit;
}

class EnhancedPHPStringFinder {

    private $maxFileSize = 500000; // Skip files larger than this size (in bytes).

    public function __construct() {
        add_action('admin_menu', array($this, 'adminMenu'));
    }

    public function adminMenu() {
        add_management_page(
            'PHP String Finder', 
            'PHP String Finder', 
            'manage_options', 
            'php-string-finder', 
            array($this, 'createAdminPage')
        );
    }

    public function createAdminPage() {
        ?>
        <div class="wrap">
            <h2>Enhanced PHP String Finder</h2>
            <form method="post">
                <?php wp_nonce_field('enhanced_php_string_finder_search'); ?>
                <p>
                    <label for="string_search">Enter String to Search:</label>
                    <input type="text" name="string_search" required />
                </p>
                <input type="submit" name="search_string" class="button button-primary" value="Search" />
            </form>
        </div>

        <?php
        if (isset($_POST['search_string'])) {
            if (!wp_verify_nonce($_POST['_wpnonce'], 'enhanced_php_string_finder_search')) {
                die('Invalid request.');
            }

            $search = stripslashes(sanitize_text_field($_POST['string_search']));
            // Set a time limit for this script to avoid timeouts on lengthy searches
            set_time_limit(600); // 10 minutes
            $this->searchStringInFiles(ABSPATH, $search); // Search in WordPress root directory
        }
    }

    private function searchStringInFiles($dir, $search) {
        try {
            $iterator = new RecursiveIteratorIterator(new RecursiveDirectoryIterator($dir));

            foreach ($iterator as $file) {
                if ($file->getExtension() === 'php' && $file->getSize() <= $this->maxFileSize) {
                    $content = file_get_contents($file->getRealPath());
                    if (strpos($content, $search) !== false) {
                        echo "<p>String found in: " . esc_html($file->getRealPath()) . "</p>";
                    }
                }
            }
        } catch (Exception $e) {
            echo "<p>Error encountered: " . esc_html($e->getMessage()) . "</p>";
        }
    }
}

// Instantiate the plugin class
new EnhancedPHPStringFinder();
?>
