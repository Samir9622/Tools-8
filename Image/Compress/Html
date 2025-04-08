<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Compression Tool</title>
    <!-- CompressorJS Library -->
    <script src="https://cdn.jsdelivr.net/npm/compressorjs@1.1.1/dist/compressor.min.js"></script>
    <style>
        :root {
            --primary-color: #3f51b5;
            --primary-dark: #303f9f;
            --primary-light: #7986cb;
            --text-color: #333;
            --text-light: #666;
            --background-color: #f8f9fa;
            --card-background: #ffffff;
            --border-color: #e0e0e0;
            --success-color: #4caf50;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --border-radius: 8px;
            --transition: all 0.3s ease;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            background-color: var(--background-color);
            padding: 20px;
        }

        .container {
            width: 100%;
            max-width: 1000px;
            margin: 0 auto;
        }

        header {
            background-color: var(--card-background);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            padding: 20px;
            margin-bottom: 20px;
        }

        .logo {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .logo h1 {
            color: var(--primary-color);
            font-size: 1.8rem;
            margin: 0;
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 20px;
        }

        nav ul li a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 500;
        }

        .subtitle {
            text-align: center;
            color: var(--text-light);
            margin-bottom: 30px;
        }

        .card {
            background-color: white;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            padding: 30px;
            margin-bottom: 20px;
        }

        .section-title {
            font-size: 1.3rem;
            color: var(--primary-color);
            margin-bottom: 20px;
            text-align: center;
        }

        .drop-area {
            border: 2px dashed var(--primary-color);
            border-radius: var(--border-radius);
            padding: 40px 20px;
            text-align: center;
            cursor: pointer;
            transition: var(--transition);
            margin-bottom: 20px;
        }

        .drop-area:hover {
            background-color: rgba(63, 81, 181, 0.05);
        }

        .drop-area.highlight {
            border-color: var(--success-color);
            background-color: rgba(76, 175, 80, 0.1);
        }

        .drop-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
            color: var(--primary-color);
        }

        .drop-area p {
            margin-bottom: 15px;
        }

        .divider {
            display: flex;
            align-items: center;
            margin: 15px 0;
            color: var(--text-light);
        }

        .divider:before, .divider:after {
            content: "";
            flex: 1;
            border-bottom: 1px solid var(--border-color);
        }

        .divider:before {
            margin-right: 10px;
        }

        .divider:after {
            margin-left: 10px;
        }

        .btn {
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 4px;
            padding: 10px 20px;
            font-size: 1rem;
            cursor: pointer;
            transition: var(--transition);
        }

        .btn:hover {
            background-color: var(--primary-dark);
        }

        .btn-secondary {
            background-color: #f0f0f0;
            color: var(--text-color);
        }

        .btn-secondary:hover {
            background-color: #e0e0e0;
        }

        .setting-group {
            margin-bottom: 20px;
        }

        .setting-group label {
            display: block;
            font-weight: 500;
            margin-bottom: 8px;
        }

        .slider-container {
            display: flex;
            align-items: center;
        }

        .slider {
            flex: 1;
            height: 5px;
            background-color: #ddd;
            outline: none;
            -webkit-appearance: none;
            border-radius: 5px;
        }

        .slider::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 20px;
            height: 20px;
            border-radius: 50%;
            background: var(--primary-color);
            cursor: pointer;
        }

        .slider-value {
            margin-left: 15px;
            font-weight: 500;
            min-width: 45px;
        }

        .quality-labels {
            display: flex;
            justify-content: space-between;
            margin-top: 5px;
            font-size: 0.8rem;
            color: var(--text-light);
        }

        select {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            font-size: 1rem;
            background-color: white;
        }

        .checkbox-group {
            display: flex;
            align-items: center;
        }

        .checkbox-group input {
            margin-right: 10px;
        }

        .preview-section {
            margin-top: 30px;
            display: none;
        }

        .preview-container {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
        }

        .original-preview, .compressed-preview {
            flex: 1;
            min-width: 300px;
        }

        .preview-header {
            font-size: 1.1rem;
            margin-bottom: 10px;
            color: var(--primary-color);
        }

        .image-preview {
            width: 100%;
            height: 300px;
            border-radius: 4px;
            overflow: hidden;
            background-color: #f5f5f5;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-bottom: 15px;
        }

        .image-preview img {
            max-width: 100%;
            max-height: 100%;
            object-fit: contain;
        }

        .file-info {
            display: flex;
            justify-content: space-between;
            font-size: 0.9rem;
            color: var(--text-light);
            margin-bottom: 15px;
        }

        .savings {
            color: var(--success-color);
            font-weight: 500;
        }

        .download-btn {
            width: 100%;
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 4px;
            padding: 10px;
            font-size: 1rem;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
        }

        .download-btn:hover {
            background-color: var(--primary-dark);
        }

        .download-icon {
            font-size: 1.2rem;
        }

        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-top: 40px;
        }

        .feature-card {
            padding: 20px;
            border-radius: var(--border-radius);
            background-color: white;
            box-shadow: var(--shadow);
        }

        .feature-card h3 {
            color: var(--primary-color);
            margin-bottom: 10px;
        }

        footer {
            text-align: center;
            padding: 20px;
            margin-top: 40px;
            color: var(--text-light);
            font-size: 0.9rem;
        }

        @media (max-width: 768px) {
            .preview-container {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <div class="logo">
                <h1>Image Compression Tool</h1>
                <nav>
                    <ul>
                        <li><a href="#">Home</a></li>
                        <li><a href="#">About</a></li>
                    </ul>
                </nav>
            </div>
        </header>

        <p class="subtitle">Reduce image size without losing quality</p>

        <div class="card">
            <h2 class="section-title">Compress Your Images</h2>
            
            <div class="drop-area" id="dropArea">
                <div class="drop-icon">📷</div>
                <p>Drag & Drop Your Images Here</p>
                <div class="divider">Or</div>
                <button class="btn" id="browseButton">Browse Files</button>
                <input type="file" id="fileInput" accept="image/*" style="display: none;">
            </div>

            <div id="imageCounter" style="display: none; text-align: center; margin-bottom: 20px;">
                <p>Selected Images: <span id="selectedCount">0</span></p>
                <button class="btn btn-secondary" id="clearButton">Clear Selection</button>
            </div>
            
            <div class="setting-group">
                <label for="qualitySlider">Compression Level: <span id="qualityValue">80%</span></label>
                <div class="slider-container">
                    <input type="range" class="slider" id="qualitySlider" min="1" max="100" value="80">
                </div>
                <div class="quality-labels">
                    <span>Higher Quality</span>
                    <span>Smaller Size</span>
                </div>
            </div>
            
            <div class="setting-group">
                <label for="formatSelect">Output Format</label>
                <select id="formatSelect">
                    <option value="image/jpeg">JPEG</option>
                    <option value="image/png">PNG</option>
                    <option value="image/webp">WebP</option>
                </select>
            </div>
            
            <div class="setting-group checkbox-group">
                <input type="checkbox" id="maintainDimensions" checked>
                <label for="maintainDimensions">Maintain original dimensions</label>
            </div>

            <button class="btn" id="compressButton" disabled>Compress Images</button>
        </div>

        <div class="preview-section" id="previewSection">
            <div class="card">
                <h2 class="section-title">Compression Results</h2>
                <div class="preview-container">
                    <div class="original-preview">
                        <h3 class="preview-header">Original</h3>
                        <div class="image-preview" id="originalPreview"></div>
                        <div class="file-info">
                            <span>Size: <span id="originalSize">-</span></span>
                        </div>
                    </div>
                    <div class="compressed-preview">
                        <h3 class="preview-header">Compressed</h3>
                        <div class="image-preview" id="compressedPreview"></div>
                        <div class="file-info">
                            <span>Size: <span id="compressedSize">-</span></span>
                            <span class="savings">Saved: <span id="savedPercentage">-</span></span>
                        </div>
                        <button class="download-btn" id="downloadButton">
                            <span class="download-icon">↓</span> Download Compressed Image
                        </button>
                    </div>
                </div>
            </div>
        </div>

        <div class="features">
            <div class="feature-card">
                <h3>Fast Processing</h3>
                <p>Our tool compresses your images in seconds using advanced algorithms to reduce file size without noticeable quality loss.</p>
            </div>
            <div class="feature-card">
                <h3>Secure & Private</h3>
                <p>All image processing happens in your browser. Your files never leave your device, ensuring complete privacy.</p>
            </div>
            <div class="feature-card">
                <h3>100% Free</h3>
                <p>No watermarks, no registration, no hidden fees. Compress as many images as you want, completely free.</p>
            </div>
        </div>

        <footer>
            <p>&copy; 2025 Image Compression Tool. All rights reserved.</p>
        </footer>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // DOM Elements
            const dropArea = document.getElementById('dropArea');
            const browseButton = document.getElementById('browseButton');
            const fileInput = document.getElementById('fileInput');
            const qualitySlider = document.getElementById('qualitySlider');
            const qualityValue = document.getElementById('qualityValue');
            const formatSelect = document.getElementById('formatSelect');
            const maintainDimensions = document.getElementById('maintainDimensions');
            const compressButton = document.getElementById('compressButton');
            const previewSection = document.getElementById('previewSection');
            const imageCounter = document.getElementById('imageCounter');
            const selectedCount = document.getElementById('selectedCount');
            const clearButton = document.getElementById('clearButton');

            // Selected files storage
            let selectedFiles = [];

            // Initialize UI
            qualityValue.textContent = qualitySlider.value + '%';

            // Event Listeners
            browseButton.addEventListener('click', function() {
                fileInput.click();
            });

            fileInput.addEventListener('change', function(e) {
                if (e.target.files.length > 0) {
                    selectedFiles = Array.from(e.target.files);
                    updateImageCounter();
                    handleFiles(selectedFiles);
                }
            });

            dropArea.addEventListener('dragover', function(e) {
                e.preventDefault();
                dropArea.classList.add('highlight');
            });

            dropArea.addEventListener('dragleave', function() {
                dropArea.classList.remove('highlight');
            });

            dropArea.addEventListener('drop', function(e) {
                e.preventDefault();
                dropArea.classList.remove('highlight');
                
                if (e.dataTransfer.files.length > 0) {
                    selectedFiles = Array.from(e.dataTransfer.files);
                    updateImageCounter();
                    handleFiles(selectedFiles);
                }
            });

            qualitySlider.addEventListener('input', function() {
                qualityValue.textContent = this.value + '%';
            });

            clearButton.addEventListener('click', function() {
                selectedFiles = [];
                fileInput.value = '';
                updateImageCounter();
                previewSection.style.display = 'none';
                compressButton.disabled = true;
            });

            compressButton.addEventListener('click', function() {
                if (selectedFiles.length > 0) {
                    compressImage(selectedFiles[0]);
                }
            });

            // Functions
            function updateImageCounter() {
                if (selectedFiles.length > 0) {
                    selectedCount.textContent = selectedFiles.length;
                    imageCounter.style.display = 'block';
                    compressButton.disabled = false;
                } else {
                    imageCounter.style.display = 'none';
                    compressButton.disabled = true;
                }
            }

            function handleFiles(files) {
                if (!files.length) return;
                
                // Filter for image files only
                const imageFiles = Array.from(files).filter(file => file.type.startsWith('image/'));
                
                if (imageFiles.length === 0) {
                    alert('Please select at least one image file');
                    return;
                }
                
                // Display original image preview
                displayOriginalImage(imageFiles[0]);
            }

            function displayOriginalImage(file) {
                const originalPreview = document.getElementById('originalPreview');
                originalPreview.innerHTML = '';
                
                const img = document.createElement('img');
                img.src = URL.createObjectURL(file);
                img.onload = function() {
                    URL.revokeObjectURL(this.src);
                };
                originalPreview.appendChild(img);
                
                document.getElementById('originalSize').textContent = formatFileSize(file.size);
                previewSection.style.display = 'block';
                
                // Auto compress after preview
                compressImage(file);
            }

            function compressImage(file) {
                const quality = parseInt(qualitySlider.value) / 100;
                const format = formatSelect.value;
                const keepDimensions = maintainDimensions.checked;
                
                new Compressor(file, {
                    quality: quality,
                    mimeType: format,
                    width: keepDimensions ? undefined : undefined,
                    height: keepDimensions ? undefined : undefined,
                    success(result) {
                        displayCompressedImage(result, file.size);
                    },
                    error(err) {
                        console.error('Compression error:', err);
                        alert('Error compressing image. Please try again with a different image.');
                    }
                });
            }

            function displayCompressedImage(file, originalSize) {
                const compressedPreview = document.getElementById('compressedPreview');
                compressedPreview.innerHTML = '';
                
                const img = document.createElement('img');
                img.src = URL.createObjectURL(file);
                img.onload = function() {
                    URL.revokeObjectURL(this.src);
                };
                compressedPreview.appendChild(img);
                
                document.getElementById('compressedSize').textContent = formatFileSize(file.size);
                
                const savedBytes = originalSize - file.size;
                const savedPercent = Math.round((savedBytes / originalSize) * 100);
                document.getElementById('savedPercentage').textContent = savedPercent + '%';
                
                setupDownloadButton(file);
            }

            function setupDownloadButton(file) {
                const downloadButton = document.getElementById('downloadButton');
                
                downloadButton.onclick = function() {
                    co
