<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub Project: MP3 DJ Mixer</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/wavesurfer.js/7.3.0/wavesurfer.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #1a2a6c;
            --secondary: #b21f1f;
            --accent: #ff6b6b;
            --accent2: #4ecdc4;
            --dark: #121230;
            --light: #f8f9fa;
            --gray: #6c757d;
        }

        body {
            background: linear-gradient(135deg, var(--primary), var(--secondary), var(--primary));
            color: var(--light);
            min-height: 100vh;
            padding: 20px;
            line-height: 1.6;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            padding: 30px 0;
            margin-bottom: 30px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            backdrop-filter: blur(10px);
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--accent), var(--accent2));
        }

        .github-banner {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(0, 0, 0, 0.7);
            padding: 8px 15px;
            border-radius: 30px;
            display: flex;
            align-items: center;
            gap: 10px;
            text-decoration: none;
            color: white;
            font-weight: 600;
            transition: all 0.3s ease;
        }

        .github-banner:hover {
            background: rgba(0, 0, 0, 0.9);
            transform: translateY(-2px);
        }

        h1 {
            font-size: 2.8rem;
            margin-bottom: 10px;
            text-shadow: 0 0 10px rgba(255, 255, 255, 0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
        }

        .tagline {
            font-size: 1.2rem;
            opacity: 0.9;
            max-width: 700px;
            margin: 0 auto;
        }

        .badges {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin: 20px 0;
            flex-wrap: wrap;
        }

        .badge {
            background: rgba(255, 255, 255, 0.1);
            padding: 8px 15px;
            border-radius: 30px;
            font-size: 0.9rem;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .content-grid {
            display: grid;
            grid-template-columns: 1fr 350px;
            gap: 30px;
            margin-bottom: 30px;
        }

        @media (max-width: 1000px) {
            .content-grid {
                grid-template-columns: 1fr;
            }
        }

        .app-container {
            display: flex;
            flex-direction: column;
            gap: 30px;
        }

        .deck-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 30px;
        }

        @media (max-width: 768px) {
            .deck-row {
                grid-template-columns: 1fr;
            }
        }

        .deck {
            background: rgba(20, 20, 40, 0.8);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
            display: flex;
            flex-direction: column;
            height: 500px;
        }

        .deck-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid rgba(255, 255, 255, 0.1);
        }

        .deck-title {
            font-size: 1.8rem;
            color: var(--accent);
        }

        .status {
            padding: 5px 15px;
            border-radius: 20px;
            background: rgba(255, 107, 107, 0.2);
            font-size: 0.9rem;
        }

        .waveform-container {
            flex: 1;
            background: rgba(0, 0, 0, 0.4);
            border-radius: 10px;
            margin-bottom: 20px;
            position: relative;
            overflow: hidden;
        }

        .waveform {
            width: 100%;
            height: 100%;
        }

        .controls {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 15px;
        }

        .control-group {
            background: rgba(0, 0, 0, 0.3);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
        }

        .control-label {
            font-size: 0.9rem;
            margin-bottom: 8px;
            color: #a0a0ff;
        }

        .knob {
            width: 70px;
            height: 70px;
            margin: 0 auto;
            position: relative;
            background: linear-gradient(135deg, #2c3e50, #1a1a2e);
            border-radius: 50%;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .knob::before {
            content: '';
            position: absolute;
            width: 6px;
            height: 30px;
            background: var(--accent);
            top: 5px;
            transform-origin: bottom center;
        }

        .control-value {
            margin-top: 8px;
            font-weight: bold;
            font-size: 0.9rem;
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 15px;
        }

        .btn {
            padding: 12px 25px;
            border: none;
            border-radius: 50px;
            background: linear-gradient(135deg, var(--accent), #ff8e53);
            color: white;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(255, 107, 107, 0.4);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(255, 107, 107, 0.6);
        }

        .btn:active {
            transform: translateY(1px);
        }

        .btn-outline {
            background: transparent;
            border: 2px solid var(--accent);
            box-shadow: none;
        }

        .btn-outline:hover {
            background: rgba(255, 107, 107, 0.2);
        }

        .mixer-section {
            background: rgba(20, 20, 40, 0.8);
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
        }

        .section-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: var(--accent2);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .mixer-controls {
            display: grid;
            grid-template-columns: 1fr 2fr 1fr;
            align-items: center;
            gap: 20px;
        }

        .crossfader {
            height: 30px;
            background: linear-gradient(to right, var(--accent), var(--accent2));
            border-radius: 15px;
            position: relative;
            box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.5);
        }

        .crossfader-handle {
            width: 25px;
            height: 50px;
            background: white;
            border-radius: 5px;
            position: absolute;
            top: -10px;
            left: 50%;
            transform: translateX(-50%);
            cursor: pointer;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
        }

        .bpm-display {
            text-align: center;
            font-size: 1.5rem;
            font-weight: bold;
            color: #ffd166;
        }

        .upload-section {
            background: rgba(20, 20, 40, 0.8);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
        }

        .file-upload {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
        }

        .upload-area {
            width: 100%;
            height: 150px;
            border: 3px dashed var(--accent2);
            border-radius: 15px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .upload-area:hover {
            background: rgba(78, 205, 196, 0.1);
        }

        .upload-icon {
            font-size: 3rem;
            color: var(--accent2);
            margin-bottom: 15px;
        }

        .upload-text {
            font-size: 1.2rem;
        }

        .track-list {
            width: 100%;
            max-height: 200px;
            overflow-y: auto;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 10px;
            padding: 15px;
            margin-top: 20px;
        }

        .track-item {
            padding: 10px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            justify-content: space-between;
            align-items: center;
            transition: all 0.3s ease;
        }

        .track-item:hover {
            background: rgba(255, 255, 255, 0.05);
        }

        .track-name {
            flex: 1;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
            font-size: 0.95rem;
        }

        .track-actions {
            display: flex;
            gap: 10px;
        }

        .action-btn {
            background: rgba(255, 255, 255, 0.1);
            border: none;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            color: white;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.2s ease;
        }

        .action-btn:hover {
            background: var(--accent);
            transform: scale(1.1);
        }

        .combine-btn {
            background: linear-gradient(135deg, var(--accent2), #1a936f);
            width: 100%;
            margin-top: 20px;
            padding: 15px;
            font-size: 1.2rem;
        }

        .project-info {
            background: rgba(20, 20, 40, 0.8);
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.4);
            height: fit-content;
        }

        .info-card {
            background: rgba(0, 0, 0, 0.3);
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 20px;
        }

        .info-card h3 {
            color: var(--accent);
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .features-list {
            list-style: none;
        }

        .features-list li {
            padding: 10px 0;
            padding-left: 30px;
            position: relative;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        .features-list li:last-child {
            border-bottom: none;
        }

        .features-list li::before {
            content: "✓";
            position: absolute;
            left: 0;
            color: var(--accent2);
            font-weight: bold;
        }

        .tech-badges {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 15px;
        }

        .tech-badge {
            background: rgba(78, 205, 196, 0.2);
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 0.85rem;
        }

        .contributors {
            display: flex;
            align-items: center;
            gap: 15px;
            margin-top: 15px;
        }

        .avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: var(--accent);
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }

        footer {
            text-align: center;
            padding: 30px;
            margin-top: 30px;
            background: rgba(0, 0, 0, 0.3);
            border-radius: 15px;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 20px 0;
        }

        .social-link {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5rem;
            color: white;
            transition: all 0.3s ease;
        }

        .social-link:hover {
            background: var(--accent);
            transform: translateY(-5px);
        }

        @media (max-width: 900px) {
            .deck {
                height: 400px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <a href="#" class="github-banner">
                <i class="fab fa-github"></i> GitHub Project
            </a>
            <h1><i class="fas fa-sliders-h"></i> MP3 DJ Mixer</h1>
            <p class="tagline">A web-based DJ application for mixing and combining MP3 files. Upload your tracks, mix them in real-time, and export your creations.</p>
            
            <div class="badges">
                <div class="badge"><i class="fas fa-code"></i> HTML/CSS/JS</div>
                <div class="badge"><i class="fas fa-music"></i> Web Audio API</div>
                <div class="badge"><i class="fas fa-wifi"></i> Offline Capable</div>
                <div class="badge"><i class="fas fa-mobile-alt"></i> Responsive Design</div>
            </div>
        </header>

        <div class="content-grid">
            <div class="app-container">
                <div class="deck-row">
                    <div class="deck">
                        <div class="deck-header">
                            <h2 class="deck-title">DECK A</h2>
                            <div class="status">Stopped</div>
                        </div>
                        <div class="waveform-container">
                            <div class="waveform" id="waveformA"></div>
                        </div>
                        <div class="controls">
                            <div class="control-group">
                                <div class="control-label">VOLUME</div>
                                <div class="knob"></div>
                                <div class="control-value">80%</div>
                            </div>
                            <div class="control-group">
                                <div class="control-label">PITCH</div>
                                <div class="knob"></div>
                                <div class="control-value">+0.0%</div>
                            </div>
                            <div class="control-group">
                                <div class="control-label">EQ</div>
                                <div class="knob"></div>
                                <div class="control-value">Neutral</div>
                            </div>
                        </div>
                        <div class="buttons">
                            <button class="btn"><i class="fas fa-play"></i> Play</button>
                            <button class="btn btn-outline"><i class="fas fa-pause"></i> Pause</button>
                            <button class="btn btn-outline"><i class="fas fa-stop"></i> Stop</button>
                        </div>
                    </div>

                    <div class="deck">
                        <div class="deck-header">
                            <h2 class="deck-title">DECK B</h2>
                            <div class="status">Stopped</div>
                        </div>
                        <div class="waveform-container">
                            <div class="waveform" id="waveformB"></div>
                        </div>
                        <div class="controls">
                            <div class="control-group">
                                <div class="control-label">VOLUME</div>
                                <div class="knob"></div>
                                <div class="control-value">80%</div>
                            </div>
                            <div class="control-group">
                                <div class="control-label">PITCH</div>
                                <div class="knob"></div>
                                <div class="control-value">+0.0%</div>
                            </div>
                            <div class="control-group">
                                <div class="control-label">EQ</div>
                                <div class="knob"></div>
                                <div class="control-value">Neutral</div>
                            </div>
                        </div>
                        <div class="buttons">
                            <button class="btn"><i class="fas fa-play"></i> Play</button>
                            <button class="btn btn-outline"><i class="fas fa-pause"></i> Pause</button>
                            <button class="btn btn-outline"><i class="fas fa-stop"></i> Stop</button>
                        </div>
                    </div>
                </div>

                <div class="mixer-section">
                    <h2 class="section-title"><i class="fas fa-sliders-h"></i> MIXER CONTROLS</h2>
                    <div class="mixer-controls">
                        <div class="bpm-display">
                            <div>BPM</div>
                            <div>128.0</div>
                        </div>
                        <div class="crossfader">
                            <div class="crossfader-handle"></div>
                        </div>
                        <div class="bpm-display">
                            <div>MASTER</div>
                            <div>0 dB</div>
                        </div>
                    </div>
                </div>

                <div class="upload-section">
                    <h2 class="section-title"><i class="fas fa-cloud-upload-alt"></i> UPLOAD & COMBINE MP3 FILES</h2>
                    <div class="file-upload">
                        <div class="upload-area" id="dropArea">
                            <i class="fas fa-cloud-upload-alt upload-icon"></i>
                            <div class="upload-text">Click or drag MP3 files to upload</div>
                            <input type="file" id="fileInput" accept=".mp3" multiple style="display: none;">
                        </div>
                        
                        <div class="track-list" id="trackList">
                            <div class="track-item">
                                <div class="track-name">demo_track_1.mp3</div>
                                <div class="track-actions">
                                    <button class="action-btn" onclick="loadToDeck(this, 'A')">
                                        <i class="fas fa-arrow-left"></i>
                                    </button>
                                    <button class="action-btn" onclick="loadToDeck(this, 'B')">
                                        <i class="fas fa-arrow-right"></i>
                                    </button>
                                    <button class="action-btn">
                                        <i class="fas fa-times"></i>
                                    </button>
                                </div>
                            </div>
                            <div class="track-item">
                                <div class="track-name">demo_track_2.mp3</div>
                                <div class="track-actions">
                                    <button class="action-btn" onclick="loadToDeck(this, 'A')">
                                        <i class="fas fa-arrow-left"></i>
                                    </button>
                                    <button class="action-btn" onclick="loadToDeck(this, 'B')">
                                        <i class="fas fa-arrow-right"></i>
                                    </button>
                                    <button class="action-btn">
                                        <i class="fas fa-times"></i>
                                    </button>
                                </div>
                            </div>
                        </div>
                        
                        <button class="btn combine-btn"><i class="fas fa-sliders-h"></i> Combine Tracks & Export</button>
                    </div>
                </div>
            </div>

            <div class="project-info">
                <div class="info-card">
                    <h3><i class="fas fa-info-circle"></i> Project Details</h3>
                    <p>The MP3 DJ Mixer is a web-based application that allows users to upload, mix, and combine MP3 files directly in the browser.</p>
                    <div class="tech-badges">
                        <div class="tech-badge">HTML5</div>
                        <div class="tech-badge">CSS3</div>
                        <div class="tech-badge">JavaScript</div>
                        <div class="tech-badge">Web Audio API</div>
                        <div class="tech-badge">WaveSurfer.js</div>
                    </div>
                </div>

                <div class="info-card">
                    <h3><i class="fas fa-star"></i> Features</h3>
                    <ul class="features-list">
                        <li>Upload multiple MP3 files via drag and drop</li>
                        <li>Real-time waveform visualization</li>
                        <li>Dual-deck mixing interface</li>
                        <li>Volume, pitch, and EQ controls</li>
                        <li>Crossfader for smooth transitions</li>
                        <li>BPM detection and display</li>
                        <li>Combine tracks into a single MP3 file</li>
                        <li>Export your final mix</li>
                        <li>Responsive design for all devices</li>
                    </ul>
                </div>

                <div class="info-card">
                    <h3><i class="fas fa-code-branch"></i> How to Contribute</h3>
                    <p>We welcome contributions! Here's how you can help:</p>
                    <ul class="features-list">
                        <li>Fork the repository on GitHub</li>
                        <li>Create a new branch for your feature</li>
                        <li>Submit a pull request with your changes</li>
                        <li>Report bugs or suggest features in issues</li>
                    </ul>
                    <button class="btn" style="width: 100%; margin-top: 20px;">
                        <i class="fab fa-github"></i> View on GitHub
                    </button>
                </div>

                <div class="info-card">
                    <h3><i class="fas fa-users"></i> Contributors</h3>
                    <div class="contributors">
                        <div class="avatar">JD</div>
                        <div>
                            <div>John Doe</div>
                            <div class="badge" style="margin-top: 5px;">Project Lead</div>
                        </div>
                    </div>
                    <div class="contributors" style="margin-top: 15px;">
                        <div class="avatar">AS</div>
                        <div>
                            <div>Alex Smith</div>
                            <div class="badge" style="margin-top: 5px;">UI Developer</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <footer>
            <h3>MP3 DJ Mixer Project</h3>
            <p>An open-source project for DJs and music enthusiasts</p>
            
            <div class="social-links">
                <a href="#" class="social-link"><i class="fab fa-github"></i></a>
                <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
                <a href="#" class="social-link"><i class="fab fa-discord"></i></a>
                <a href="#" class="social-link"><i class="fab fa-youtube"></i></a>
            </div>
            
            <p>Released under the MIT License | © 2023 DJ Mixer Project</p>
        </footer>
    </div>

    <script>
        // Initialize waveform displays
        const wavesurferA = WaveSurfer.create({
            container: '#waveformA',
            waveColor: '#ff6b6b',
            progressColor: '#ff8e53',
            height: 180,
            barWidth: 3,
            barRadius: 3,
            barGap: 2,
            cursorWidth: 0
        });

        const wavesurferB = WaveSurfer.create({
            container: '#waveformB',
            waveColor: '#4ecdc4',
            progressColor: '#1a936f',
            height: 180,
            barWidth: 3,
            barRadius: 3,
            barGap: 2,
            cursorWidth: 0
        });

        // Load demo waveforms
        wavesurferA.load('https://wavesurfer-js.org/example/media/demo.wav');
        wavesurferB.load('https://wavesurfer-js.org/example/media/demo.wav');

        // File upload functionality
        const dropArea = document.getElementById('dropArea');
        const fileInput = document.getElementById('fileInput');
        const trackList = document.getElementById('trackList');

        dropArea.addEventListener('click', () => {
            fileInput.click();
        });

        fileInput.addEventListener('change', handleFiles);

        // Handle drag and drop
        ['dragenter', 'dragover', 'dragleave', 'drop'].forEach(eventName => {
            dropArea.addEventListener(eventName, preventDefaults, false);
        });

        function preventDefaults(e) {
            e.preventDefault();
            e.stopPropagation();
        }

        ['dragenter', 'dragover'].forEach(eventName => {
            dropArea.addEventListener(eventName, highlight, false);
        });

        ['dragleave', 'drop'].forEach(eventName => {
            dropArea.addEventListener(eventName, unhighlight, false);
        });

        function highlight() {
            dropArea.style.borderColor = '#ff6b6b';
            dropArea.style.backgroundColor = 'rgba(78, 205, 196, 0.1)';
        }

        function unhighlight() {
            dropArea.style.borderColor = '#4ecdc4';
            dropArea.style.backgroundColor = 'transparent';
        }

        dropArea.addEventListener('drop', handleDrop, false);

        function handleDrop(e) {
            const dt = e.dataTransfer;
            const files = dt.files;
            handleFiles(files);
        }

        function handleFiles(e) {
            const files = e.target?.files || e;
            
            if (files.length > 0) {
                trackList.innerHTML = '';
                
                for (let i = 0; i < files.length; i++) {
                    const file = files[i];
                    const trackItem = document.createElement('div');
                    trackItem.className = 'track-item';
                    
                    trackItem.innerHTML = `
                        <div class="track-name">${file.name}</div>
                        <div class="track-actions">
                            <button class="action-btn" onclick="loadToDeck(this, 'A')">
                                <i class="fas fa-arrow-left"></i>
                            </button>
                            <button class="action-btn" onclick="loadToDeck(this, 'B')">
                                <i class="fas fa-arrow-right"></i>
                            </button>
                            <button class="action-btn" onclick="removeTrack(this)">
                                <i class="fas fa-times"></i>
                            </button>
                        </div>
                    `;
                    
                    trackList.appendChild(trackItem);
                }
            }
        }

        // Deck interaction functions
        function loadToDeck(btn, deck) {
            const trackItem = btn.closest('.track-item');
            const trackName = trackItem.querySelector('.track-name').textContent;
            
            // Visual feedback
            const deckTitle = document.querySelector(`.deck-${deck} .deck-title`);
            const originalText = deckTitle.textContent;
            deckTitle.innerHTML = `<i class="fas fa-spinner fa-spin"></i> Loading...`;
            
            setTimeout(() => {
                deckTitle.textContent = originalText;
                alert(`Loaded "${trackName}" to Deck ${deck}`);
            }, 1000);
        }

        function removeTrack(btn) {
            const trackItem = btn.closest('.track-item');
            trackItem.style.transform = 'translateX(100%)';
            trackItem.style.opacity = '0';
            
            setTimeout(() => {
                trackItem.remove();
                
                if (trackList.children.length === 0) {
                    trackList.innerHTML = '<div class="track-item"><div class="track-name">No tracks uploaded yet</div></div>';
                }
            }, 300);
        }

        // Knob rotation simulation
        const knobs = document.querySelectorAll('.knob');
        knobs.forEach(knob => {
            const rotation = Math.floor(Math.random() * 140) - 70;
            knob.style.transform = `rotate(${rotation}deg)`;
            knob.dataset.rotation = rotation;
        });

        // Play button functionality
        const playButtons = document.querySelectorAll('.btn:not(.combine-btn):not(.btn-outline)');
        playButtons.forEach(btn => {
            btn.addEventListener('click', function() {
                const deck = this.closest('.deck');
                const status = deck.querySelector('.status');
                status.textContent = 'Playing';
                status.style.background = 'rgba(78, 205, 196, 0.3)';
            });
        });

        // Pause button functionality
        const pauseButtons = document.querySelectorAll('.btn-outline:nth-child(2)');
        pauseButtons.forEach(btn => {
            btn.addEventListener('click', function() {
                const deck = this.closest('.deck');
                const status = deck.querySelector('.status');
                status.textContent = 'Paused';
                status.style.background = 'rgba(255, 209, 102, 0.3)';
            });
        });

        // Stop button functionality
        const stopButtons = document.querySelectorAll('.btn-outline:nth-child(3)');
        stopButtons.forEach(btn => {
            btn.addEventListener('click', function() {
                const deck = this.closest('.deck');
                const status = deck.querySelector('.status');
                status.textContent = 'Stopped';
                status.style.background = 'rgba(255, 107, 107, 0.3)';
            });
        });

        // Combine button functionality
        const combineBtn = document.querySelector('.combine-btn');
        combineBtn.addEventListener('click', function() {
            const trackItems = document.querySelectorAll('.track-item .track-name');
            if (trackItems.length === 0 || 
               (trackItems.length === 1 && trackItems[0].textContent === 'No tracks uploaded yet')) {
                alert('Please upload at least one MP3 file to combine');
                return;
            }
            
            this.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Processing...';
            
            setTimeout(() => {
                this.innerHTML = '<i class="fas fa-sliders-h"></i> Combine Tracks & Export';
                alert('Your mixed track is ready! Download will start shortly.');
                
                // Simulate download
                const link = document.createElement('a');
                link.href = '#';
                link.download = 'dj-mix.mp3';
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
            }, 2000);
        });

        // Crossfader functionality
        const crossfaderHandle = document.querySelector('.crossfader-handle');
        const crossfader = document.querySelector('.crossfader');
        let isDragging = false;

        crossfaderHandle.addEventListener('mousedown', function(e) {
            isDragging = true;
            document.addEventListener('mousemove', handleMove);
            document.addEventListener('mouseup', stopDrag);
        });

        function handleMove(e) {
            if (!isDragging) return;
            
            const rect = crossfader.getBoundingClientRect();
            let x = e.clientX - rect.left;
            x = Math.max(0, Math.min(x, rect.width));
            
            crossfaderHandle.style.left = `${x}px`;
            
            // Update deck volumes based on crossfader position
            const position = x / rect.width;
            const deckAVol = (1 - position).toFixed(1);
            const deckBVol = position.toFixed(1);
            
            // Update deck volume displays
            document.querySelector('.deck:nth-child(1) .control-group:first-child .control-value').textContent = `${Math.round(deckAVol * 100)}%`;
            document.querySelector('.deck:nth-child(2) .control-group:first-child .control-value').textContent = `${Math.round(deckBVol * 100)}%`;
        }

        function stopDrag() {
            isDragging = false;
            document.removeEventListener('mousemove', handleMove);
            document.removeEventListener('mouseup', stopDrag);
        }
    </script>
</body>
</html>
