<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GitHub MP3 Manager</title>
    <script src="https://cdn.tailwindcss.com/3.4.16"></script>
    <script>tailwind.config={theme:{extend:{colors:{primary:'#0969da',secondary:'#24292f'},borderRadius:{'none':'0px','sm':'4px',DEFAULT:'8px','md':'12px','lg':'16px','xl':'20px','2xl':'24px','3xl':'32px','full':'9999px','button':'8px'}}}}</script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Pacifico&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/remixicon/4.6.0/remixicon.min.css">
    <style>
        :where([class^="ri-"])::before { content: "\f3c2"; }
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
        }
        .audio-player::-webkit-media-controls-panel {
            background-color: #f6f8fa;
        }
        .audio-player::-webkit-media-controls-play-button {
            background-color: #0969da;
            border-radius: 50%;
        }
        input[type="range"]::-webkit-slider-thumb {
            -webkit-appearance: none;
            appearance: none;
            width: 16px;
            height: 16px;
            border-radius: 50%;
            background: #0969da;
            cursor: pointer;
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-900">
    <!-- Header -->
    <header class="fixed top-0 w-full bg-white shadow-sm z-50">
        <div class="px-4 py-3 flex items-center justify-between">
            <div class="flex items-center">
                <div class="w-8 h-8 flex items-center justify-center mr-2">
                    <i class="ri-github-fill ri-lg text-gray-900"></i>
                </div>
                <h1 class="font-['Pacifico'] text-xl">logo</h1>
            </div>
            <div class="flex items-center">
                <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                    <i class="ri-notification-3-line ri-lg"></i>
                </div>
                <div class="w-8 h-8 ml-2 flex items-center justify-center cursor-pointer">
                    <i class="ri-user-line ri-lg"></i>
                </div>
            </div>
        </div>
        
        <div class="px-4 pb-2">
            <div class="flex items-center text-sm text-gray-600 mb-2">
                <span class="cursor-pointer hover:text-primary">user123</span>
                <i class="ri-arrow-right-s-line mx-1"></i>
                <span class="cursor-pointer hover:text-primary">music-project</span>
                <i class="ri-arrow-right-s-line mx-1"></i>
                <span class="text-primary">mp3-files</span>
            </div>
            
            <div class="relative">
                <input type="text" placeholder="Search files..." class="w-full px-4 py-2 pr-10 bg-gray-100 rounded-button text-sm focus:outline-none focus:ring-2 focus:ring-primary/20">
                <div class="absolute right-3 top-1/2 transform -translate-y-1/2 w-5 h-5 flex items-center justify-center cursor-pointer">
                    <i class="ri-search-line text-gray-500"></i>
                </div>
            </div>
        </div>
    </header>
    <!-- Main Content -->
    <main class="pt-28 pb-20 px-4">
        <!-- Storage Status -->
        <div class="bg-white rounded-lg shadow-sm p-4 mb-4">
            <div class="flex justify-between items-center mb-2">
                <h2 class="text-sm font-medium">Storage</h2>
                <span class="text-xs text-gray-500">2.1 GB / 5 GB</span>
            </div>
            <div class="h-2 bg-gray-100 rounded-full overflow-hidden">
                <div class="h-full bg-primary" style="width: 42%"></div>
            </div>
        </div>

        <!-- Current Path -->
        <div class="bg-white rounded-lg shadow-sm p-4 mb-4 flex items-center">
            <div class="w-8 h-8 flex items-center justify-center cursor-pointer mr-2">
                <i class="ri-arrow-left-s-line ri-lg"></i>
            </div>
            <div class="flex-1 overflow-x-auto whitespace-nowrap text-sm">
                <span class="cursor-pointer text-gray-500">music-project</span>
                <i class="ri-arrow-right-s-line mx-1 text-gray-400"></i>
                <span class="cursor-pointer text-gray-500">albums</span>
                <i class="ri-arrow-right-s-line mx-1 text-gray-400"></i>
                <span class="text-primary font-medium">summer-hits</span>
            </div>
        </div>

        <!-- Folder Section -->
        <div class="bg-white rounded-lg shadow-sm p-4 mb-4">
            <h2 class="text-sm font-medium mb-3">Folders</h2>
            <div class="grid grid-cols-3 gap-3">
                <div class="flex flex-col items-center cursor-pointer p-2 rounded-lg hover:bg-gray-50">
                    <div class="w-12 h-12 flex items-center justify-center mb-1 text-primary">
                        <i class="ri-folder-music-fill ri-2x"></i>
                    </div>
                    <span class="text-xs text-center truncate w-full">Rock Classics</span>
                </div>
                <div class="flex flex-col items-center cursor-pointer p-2 rounded-lg hover:bg-gray-50">
                    <div class="w-12 h-12 flex items-center justify-center mb-1 text-primary">
                        <i class="ri-folder-music-fill ri-2x"></i>
                    </div>
                    <span class="text-xs text-center truncate w-full">Jazz Collection</span>
                </div>
                <div class="flex flex-col items-center cursor-pointer p-2 rounded-lg hover:bg-gray-50">
                    <div class="w-12 h-12 flex items-center justify-center mb-1 text-primary">
                        <i class="ri-folder-music-fill ri-2x"></i>
                    </div>
                    <span class="text-xs text-center truncate w-full">Podcasts</span>
                </div>
            </div>
        </div>

        <!-- Files Section -->
        <div class="bg-white rounded-lg shadow-sm p-4 mb-4">
            <div class="flex justify-between items-center mb-3">
                <h2 class="text-sm font-medium">MP3 Files</h2>
                <div class="flex">
                    <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                        <i class="ri-list-check-2 ri-lg text-gray-500"></i>
                    </div>
                    <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                        <i class="ri-sort-desc ri-lg text-gray-500"></i>
                    </div>
                </div>
            </div>

            <!-- MP3 File Item -->
            <div class="border-b border-gray-100 py-3" id="file-1">
                <div class="flex items-center justify-between mb-2">
                    <div class="flex items-center">
                        <div class="w-8 h-8 flex items-center justify-center mr-3 text-primary">
                            <i class="ri-music-fill ri-lg"></i>
                        </div>
                        <div>
                            <h3 class="text-sm font-medium">Summer Vibes.mp3</h3>
                            <p class="text-xs text-gray-500">3:42 • 320 kbps • 8.5 MB</p>
                        </div>
                    </div>
                    <div class="flex">
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer" onclick="togglePlay('file-1')">
                            <i class="ri-play-fill ri-lg text-primary play-icon"></i>
                            <i class="ri-pause-fill ri-lg text-primary pause-icon hidden"></i>
                        </div>
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                            <i class="ri-download-line ri-lg text-gray-500"></i>
                        </div>
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                            <i class="ri-more-2-fill ri-lg text-gray-500"></i>
                        </div>
                    </div>
                </div>
                <div class="audio-player-container hidden">
                    <audio class="audio-player w-full h-10" controls>
                        <source src="#" type="audio/mpeg">
                    </audio>
                </div>
            </div>

            <!-- MP3 File Item -->
            <div class="border-b border-gray-100 py-3" id="file-2">
                <div class="flex items-center justify-between mb-2">
                    <div class="flex items-center">
                        <div class="w-8 h-8 flex items-center justify-center mr-3 text-primary">
                            <i class="ri-music-fill ri-lg"></i>
                        </div>
                        <div>
                            <h3 class="text-sm font-medium">Beach Party.mp3</h3>
                            <p class="text-xs text-gray-500">4:15 • 320 kbps • 9.7 MB</p>
                        </div>
                    </div>
                    <div class="flex">
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer" onclick="togglePlay('file-2')">
                            <i class="ri-play-fill ri-lg text-primary play-icon"></i>
                            <i class="ri-pause-fill ri-lg text-primary pause-icon hidden"></i>
                        </div>
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                            <i class="ri-download-line ri-lg text-gray-500"></i>
                        </div>
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                            <i class="ri-more-2-fill ri-lg text-gray-500"></i>
                        </div>
                    </div>
                </div>
                <div class="audio-player-container hidden">
                    <audio class="audio-player w-full h-10" controls>
                        <source src="#" type="audio/mpeg">
                    </audio>
                </div>
            </div>

            <!-- MP3 File Item -->
            <div class="border-b border-gray-100 py-3" id="file-3">
                <div class="flex items-center justify-between mb-2">
                    <div class="flex items-center">
                        <div class="w-8 h-8 flex items-center justify-center mr-3 text-primary">
                            <i class="ri-music-fill ri-lg"></i>
                        </div>
                        <div>
                            <h3 class="text-sm font-medium">Sunset Dreams.mp3</h3>
                            <p class="text-xs text-gray-500">5:28 • 256 kbps • 10.2 MB</p>
                        </div>
                    </div>
                    <div class="flex">
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer" onclick="togglePlay('file-3')">
                            <i class="ri-play-fill ri-lg text-primary play-icon"></i>
                            <i class="ri-pause-fill ri-lg text-primary pause-icon hidden"></i>
                        </div>
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                            <i class="ri-download-line ri-lg text-gray-500"></i>
                        </div>
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                            <i class="ri-more-2-fill ri-lg text-gray-500"></i>
                        </div>
                    </div>
                </div>
                <div class="audio-player-container hidden">
                    <audio class="audio-player w-full h-10" controls>
                        <source src="#" type="audio/mpeg">
                    </audio>
                </div>
            </div>

            <!-- MP3 File Item -->
            <div class="border-b border-gray-100 py-3" id="file-4">
                <div class="flex items-center justify-between mb-2">
                    <div class="flex items-center">
                        <div class="w-8 h-8 flex items-center justify-center mr-3 text-primary">
                            <i class="ri-music-fill ri-lg"></i>
                        </div>
                        <div>
                            <h3 class="text-sm font-medium">Ocean Waves.mp3</h3>
                            <p class="text-xs text-gray-500">6:10 • 320 kbps • 14.1 MB</p>
                        </div>
                    </div>
                    <div class="flex">
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer" onclick="togglePlay('file-4')">
                            <i class="ri-play-fill ri-lg text-primary play-icon"></i>
                            <i class="ri-pause-fill ri-lg text-primary pause-icon hidden"></i>
                        </div>
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                            <i class="ri-download-line ri-lg text-gray-500"></i>
                        </div>
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                            <i class="ri-more-2-fill ri-lg text-gray-500"></i>
                        </div>
                    </div>
                </div>
                <div class="audio-player-container hidden">
                    <audio class="audio-player w-full h-10" controls>
                        <source src="#" type="audio/mpeg">
                    </audio>
                </div>
            </div>

            <!-- MP3 File Item -->
            <div class="py-3" id="file-5">
                <div class="flex items-center justify-between mb-2">
                    <div class="flex items-center">
                        <div class="w-8 h-8 flex items-center justify-center mr-3 text-primary">
                            <i class="ri-music-fill ri-lg"></i>
                        </div>
                        <div>
                            <h3 class="text-sm font-medium">Tropical Nights.mp3</h3>
                            <p class="text-xs text-gray-500">4:52 • 320 kbps • 11.2 MB</p>
                        </div>
                    </div>
                    <div class="flex">
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer" onclick="togglePlay('file-5')">
                            <i class="ri-play-fill ri-lg text-primary play-icon"></i>
                            <i class="ri-pause-fill ri-lg text-primary pause-icon hidden"></i>
                        </div>
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                            <i class="ri-download-line ri-lg text-gray-500"></i>
                        </div>
                        <div class="w-8 h-8 flex items-center justify-center cursor-pointer">
                            <i class="ri-more-2-fill ri-lg text-gray-500"></i>
                        </div>
                    </div>
                </div>
                <div class="audio-player-container hidden">
                    <audio class="audio-player w-full h-10" controls>
                        <source src="#" type="audio/mpeg">
                    </audio>
                </div>
            </div>
        </div>

        <!-- Recent Activity -->
        <div class="bg-white rounded-lg shadow-sm p-4">
            <h2 class="text-sm font-medium mb-3">Recent Activity</h2>
            <div class="space-y-3">
                <div class="flex items-start">
                    <div class="w-8 h-8 flex items-center justify-center mr-3 text-gray-500 mt-0.5">
                        <i class="ri-upload-2-line"></i>
                    </div>
                    <div>
                        <p class="text-sm">You uploaded <span class="font-medium">Summer Vibes.mp3</span></p>
                        <p class="text-xs text-gray-500">Today, 10:23 AM</p>
                    </div>
                </div>
                <div class="flex items-start">
                    <div class="w-8 h-8 flex items-center justify-center mr-3 text-gray-500 mt-0.5">
                        <i class="ri-folder-add-line"></i>
                    </div>
                    <div>
                        <p class="text-sm">You created folder <span class="font-medium">Summer Hits</span></p>
                        <p class="text-xs text-gray-500">Today, 09:45 AM</p>
                    </div>
                </div>
                <div class="flex items-start">
                    <div class="w-8 h-8 flex items-center justify-center mr-3 text-gray-500 mt-0.5">
                        <i class="ri-share-line"></i>
                    </div>
                    <div>
                        <p class="text-sm">You shared <span class="font-medium">Beach Party.mp3</span> with <span class="font-medium">Emily Chen</span></p>
                        <p class="text-xs text-gray-500">Yesterday, 4:12 PM</p>
                    </div>
                </div>
            </div>
        </div>
    </main>

    <!-- Floating Action Button -->
    <div class="fixed right-4 bottom-20 z-40">
        <button class="w-14 h-14 bg-primary rounded-full shadow-lg flex items-center justify-center cursor-pointer" id="upload-btn">
            <i class="ri-upload-2-fill ri-lg text-white"></i>
        </button>
    </div>

    <!-- Upload Modal -->
    <div class="fixed inset-0 bg-black bg-opacity-50 z-50 flex items-center justify-center hidden" id="upload-modal">
        <div class="bg-white rounded-lg w-[90%] max-w-md">
            <div class="p-4 border-b border-gray-100">
                <h2 class="text-lg font-medium">Upload MP3 Files</h2>
            </div>
            <div class="p-4">
                <div class="border-2 border-dashed border-gray-200 rounded-lg p-6 text-center mb-4">
                    <div class="w-16 h-16 mx-auto mb-3 flex items-center justify-center text-primary">
                        <i class="ri-upload-cloud-2-line ri-3x"></i>
                    </div>
                    <p class="text-sm mb-2">Drag and drop files here or</p>
                    <button class="px-4 py-2 bg-primary text-white text-sm rounded-button cursor-pointer">Browse Files</button>
                    <p class="text-xs text-gray-500 mt-2">Supports MP3 files up to 50MB</p>
                </div>
                <div class="space-y-3 hidden" id="upload-progress">
                    <div>
                        <div class="flex justify-between text-sm mb-1">
                            <span>NewSong.mp3</span>
                            <span>75%</span>
                        </div>
                        <div class="h-2 bg-gray-100 rounded-full overflow-hidden">
                            <div class="h-full bg-primary" style="width: 75%"></div>
                        </div>
                    </div>
                </div>
            </div>
            <div class="p-4 border-t border-gray-100 flex justify-end space-x-2">
                <button class="px-4 py-2 text-sm text-gray-600 rounded-button cursor-pointer" id="cancel-upload">Cancel</button>
                <button class="px-4 py-2 bg-primary text-white text-sm rounded-button cursor-pointer">Upload</button>
            </div>
        </div>
    </div>

    <!-- Bottom Navigation -->
    <nav class="fixed bottom-0 w-full bg-white border-t border-gray-200 z-50">
        <div class="grid grid-cols-4 h-16">
            <div class="flex flex-col items-center justify-center cursor-pointer text-primary">
                <div class="w-6 h-6 flex items-center justify-center">
                    <i class="ri-folder-line ri-lg"></i>
                </div>
                <span class="text-xs mt-1">Files</span>
            </div>
            <div class="flex flex-col items-center justify-center cursor-pointer text-gray-500">
                <div class="w-6 h-6 flex items-center justify-center">
                    <i class="ri-time-line ri-lg"></i>
                </div>
                <span class="text-xs mt-1">Recent</span>
            </div>
            <div class="flex flex-col items-center justify-center cursor-pointer text-gray-500">
                <div class="w-6 h-6 flex items-center justify-center">
                    <i class="ri-star-line ri-lg"></i>
                </div>
                <span class="text-xs mt-1">Favorites</span>
            </div>
            <div class="flex flex-col items-center justify-center cursor-pointer text-gray-500">
                <div class="w-6 h-6 flex items-center justify-center">
                    <i class="ri-settings-3-line ri-lg"></i>
                </div>
                <span class="text-xs mt-1">Settings</span>
            </div>
        </div>
    </nav>

    <!-- Scripts -->
    <script id="audio-player-script">
        function togglePlay(fileId) {
            const container = document.querySelector(`#${fileId} .audio-player-container`);
            const playIcon = document.querySelector(`#${fileId} .play-icon`);
            const pauseIcon = document.querySelector(`#${fileId} .pause-icon`);
            const audio = document.querySelector(`#${fileId} .audio-player`);
            
            if (container.classList.contains('hidden')) {
                container.classList.remove('hidden');
                playIcon.classList.add('hidden');
                pauseIcon.classList.remove('hidden');
                audio.play();
            } else {
                if (audio.paused) {
                    audio.play();
                    playIcon.classList.add('hidden');
                    pauseIcon.classList.remove('hidden');
                } else {
                    audio.pause();
                    playIcon.classList.remove('hidden');
                    pauseIcon.classList.add('hidden');
                }
            }
        }
    </script>

    <script id="upload-modal-script">
        document.addEventListener('DOMContentLoaded', function() {
            const uploadBtn = document.getElementById('upload-btn');
            const uploadModal = document.getElementById('upload-modal');
            const cancelUpload = document.getElementById('cancel-upload');
            
            uploadBtn.addEventListener('click', function() {
                uploadModal.classList.remove('hidden');
            });
            
            cancelUpload.addEventListener('click', function() {
                uploadModal.classList.add('hidden');
            });
            
            uploadModal.addEventListener('click', function(e) {
                if (e.target === uploadModal) {
                    uploadModal.classList.add('hidden');
                }
            });
        });
    </script>
</body>
</html>
