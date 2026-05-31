<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>张宇涵 | 新闻传播研究者</title>
    <meta name="description" content="张宇涵 - 新闻传播学硕士研究生，喜欢关注时代新浪潮、新现象、永远对一切保持好奇、对自己的热爱保持专注">
    <meta name="keywords" content="张宇涵,新闻传播,新闻采写,数字媒体,新媒体运营">
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: '#0a3d62',
                        secondary: '#3c6382',
                        neutral: '#f5f6fa',
                        dark: '#1e272e',
                        light: '#fafafa'
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                    },
                }
            }
        }
    </script>
    <style type="text/tailwindcss">
        @layer utilities {
            .content-auto {
                content-visibility: auto;
            }
            .text-balance {
                text-wrap: balance;
            }
            .animate-fade-in {
                animation: fadeIn 0.8s cubic-bezier(0.23, 1, 0.32, 1);
            }
            .animate-slide-up {
                animation: slideUp 0.7s cubic-bezier(0.23, 1, 0.32, 1);
            }
            .animate-fade-in-scroll {
                opacity: 0;
                transform: translateY(30px);
                transition: all 0.7s cubic-bezier(0.23, 1, 0.32, 1);
            }
            .animate-fade-in-scroll.visible {
                opacity: 1;
                transform: translateY(0);
            }
            .progress-bar {
                height: 3px;
                background: #0a3d62;
                position: fixed;
                top: 0;
                left: 0;
                z-index: 50;
                transition: width 0.25s cubic-bezier(0.23, 1, 0.32, 1);
            }
            .card-hover {
                transition: transform 0.45s cubic-bezier(0.23, 1, 0.32, 1), 
                            box-shadow 0.45s cubic-bezier(0.23, 1, 0.32, 1),
                            background 0.3s ease;
            }
            .card-hover:hover {
                transform: translateY(-6px) scale(1.01);
                box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.1), 0 10px 10px -5px rgb(0 0 0 / 0.04);
            }
            .timeline-item {
                position: relative;
                padding-left: 32px;
            }
            .timeline-item::before {
                content: '';
                position: absolute;
                left: 0;
                top: 8px;
                width: 16px;
                height: 16px;
                border-radius: 50%;
                background: #0a3d62;
                transition: background 0.3s ease;
            }
            .timeline-item::after {
                content: '';
                position: absolute;
                left: 7px;
                top: 24px;
                width: 2px;
                height: calc(100% - 16px);
                background: #e2e8f0;
                transition: background 0.3s ease;
            }
            .timeline-item:last-child::after {
                display: none;
            }
            .dark .timeline-item::before {
                background: #3b82f6;
            }
            .dark .timeline-item::after {
                background: #4a5568;
            }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        @keyframes slideUp {
            from { transform: translateY(30px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        * {
            backface-visibility: hidden;
            perspective: 1000px;
            transform-style: preserve-3d;
            will-change: transform, opacity;
        }

        html {
            scroll-behavior: smooth;
            scroll-padding-top: 80px;
            transition: background-color 0.5s cubic-bezier(0.23, 1, 0.32, 1),
                        color 0.5s cubic-bezier(0.23, 1, 0.32, 1);
        }

        body {
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
            overflow-x: hidden;
        }

        nav {
            transition: transform 0.35s cubic-bezier(0.23, 1, 0.32, 1), 
                        background 0.3s ease;
        }
    </style>
</head>
<body class="bg-light dark:bg-dark text-gray-800 dark:text-gray-200 transition-colors duration-300">
    <div id="progressBar" class="progress-bar"></div>

    <nav class="fixed w-full top-0 z-40 bg-white/90 dark:bg-dark/90 backdrop-blur-md border-b border-gray-200 dark:border-gray-800 transition-all duration-300">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between h-16">
                <div class="flex items-center">
                    <a href="#" class="text-primary dark:text-blue-400 font-semibold text-xl">张宇涵</a>
                    <span class="ml-2 text-sm text-gray-500 dark:text-gray-400">News Communication</span>
                </div>
                <div class="flex items-center space-x-6">
                    <a href="#about" class="hidden sm:block hover:text-primary dark:hover:text-blue-400 transition-colors">关于</a>
                    <a href="#experience" class="hidden sm:block hover:text-primary dark:hover:text-blue-400 transition-colors">经历</a>
                    <a href="#research" class="hidden sm:block hover:text-primary dark:hover:text-blue-400 transition-colors">研究</a>
                    <a href="#portfolio" class="hidden sm:block hover:text-primary dark:hover:text-blue-400 transition-colors">作品</a>
                    <a href="#contact" class="hidden sm:block hover:text-primary dark:hover:text-blue-400 transition-colors">联系</a>
                    <button id="themeToggle" class="p-2 rounded-full hover:bg-gray-200 dark:hover:bg-gray-700 transition-colors">
                        <i class="fa fa-moon-o dark:hidden"></i>
                        <i class="fa fa-sun-o hidden dark:block"></i>
                    </button>
                </div>
            </div>
        </div>
    </nav>

    <div id="loader" class="fixed inset-0 z-50 flex items-center justify-center bg-white dark:bg-dark transition-opacity duration-500">
        <div class="animate-pulse text-primary dark:text-blue-400 text-2xl">Yuhan Zhang</div>
    </div>

    <section class="min-h-screen pt-24 pb-16 md:pb-0 flex items-center">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 w-full">
            <div class="grid md:grid-cols-2 gap-12 items-center">
                <div class="animate-slide-up">
                    <h1 class="text-5xl md:text-6xl font-bold mb-4">张宇涵</h1>
                    <h2 class="text-xl md:text-2xl text-gray-600 dark:text-gray-300 mb-6">新闻传播学硕士研究生</h2>
                    <p class="text-lg text-gray-500 dark:text-gray-400 mb-2">Researcher · Storyteller · Communicator</p>
                    <div class="w-16 h-1 bg-primary dark:bg-blue-400 my-8"></div>
                    <p class="text-lg leading-relaxed mb-8 text-balance">
                        关注数字传播、AI传播、网络健康传播与新媒体运营。<br>
                        致力于探索技术变革背景下的信息传播机制与社会影响。
                    </p>
                    <div class="flex flex-wrap gap-4">
                        <a href="#portfolio" class="px-6 py-3 bg-primary dark:bg-blue-600 text-white rounded-lg hover:bg-secondary dark:hover:bg-blue-500 transition-colors">
                            查看作品
                        </a>
                        <a href="#about" class="px-6 py-3 border border-gray-300 dark:border-gray-600 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-800 transition-colors">
                            了解更多
                        </a>
                    </div>
                </div>
                <div class="bg-white dark:bg-gray-800 p-6 rounded-2xl shadow-lg animate-fade-in card-hover">
                    <h3 class="text-xl font-semibold mb-6 border-b pb-3 border-gray-200 dark:border-gray-700">个人信息</h3>
                    <ul class="space-y-4">
                        <li class="flex items-center">
                            <span class="w-8 text-primary dark:text-blue-400"><i class="fa fa-graduation-cap"></i></span>
                            <span>中国人民大学</span>
                        </li>
                        <li class="flex items-center">
                            <span class="w-8 text-primary dark:text-blue-400"><i class="fa fa-book"></i></span>
                            <span>新闻传播学硕士</span>
                        </li>
                        <li class="flex items-center">
                            <span class="w-8 text-primary dark:text-blue-400"><i class="fa fa-pencil"></i></span>
                            <span>《中国记者》作者</span>
                        </li>
                        <li class="flex items-center">
                            <span class="w-8 text-primary dark:text-blue-400"><i class="fa fa-video-camera"></i></span>
                            <span>百万播放新闻作品创作者</span>
                        </li>
                        <li class="flex items-center">
                            <span class="w-8 text-primary dark:text-blue-400"><i class="fa fa-bar-chart"></i></span>
                            <span>新媒体传播研究</span>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <section id="about" class="py-20 bg-neutral dark:bg-gray-900">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 animate-fade-in-scroll">
            <div class="text-center mb-16">
                <h2 class="text-3xl font-bold mb-3">关于我</h2>
                <p class="text-gray-600 dark:text-gray-400">教育背景与专业特点</p>
            </div>

            <div class="mb-16">
                <h3 class="text-2xl font-semibold mb-8 text-center">教育背景</h3>
                <div class="space-y-8 max-w-3xl mx-auto">
                    <div class="timeline-item pl-8 pb-8">
                        <h4 class="text-xl font-bold">中国人民大学</h4>
                        <p class="text-primary dark:text-blue-400 font-medium">新闻传播学硕士 | 2024—2027</p>
                        <p class="text-gray-600 dark:text-gray-400 mt-2">GPA：3.77/4.0</p>
                        <div class="mt-4">
                            <h5 class="font-medium mb-2">研究方向：</h5>
                            <ul class="list-disc list-inside text-gray-600 dark:text-gray-400 space-y-1">
                                <li>数字传播</li>
                                <li>AI传播</li>
                                <li>网络健康传播</li>
                                <li>新媒体运营</li>
                            </ul>
                        </div>
                    </div>
                    <div class="timeline-item pl-8">
                        <h4 class="text-xl font-bold">北京印刷学院</h4>
                        <p class="text-primary dark:text-blue-400 font-medium">新闻学本科 | 2020—2024</p>
                        <p class="text-gray-600 dark:text-gray-400 mt-2">GPA：4.17/5.0</p>
                    </div>
                </div>
            </div>

            <div>
                <h3 class="text-2xl font-semibold mb-8 text-center">我的特点</h3>
                <div class="grid md:grid-cols-3 gap-6">
                    <div class="bg-white dark:bg-gray-800 p-6 rounded-xl shadow card-hover text-center">
                        <div class="w-12 h-12 bg-primary/10 dark:bg-blue-400/10 rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class="fa fa-file-text-o text-primary dark:text-blue-400 text-xl"></i>
                        </div>
                        <h4 class="text-lg font-bold mb-2">学术研究</h4>
                        <p class="text-gray-600 dark:text-gray-400">论文发表与课题参与</p>
                    </div>
                    <div class="bg-white dark:bg-gray-800 p-6 rounded-xl shadow card-hover text-center">
                        <div class="w-12 h-12 bg-primary/10 dark:bg-blue-400/10 rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class="fa fa-pencil-square-o text-primary dark:text-blue-400 text-xl"></i>
                        </div>
                        <h4 class="text-lg font-bold mb-2">媒体实践</h4>
                        <p class="text-gray-600 dark:text-gray-400">新闻采写与传播策划</p>
                    </div>
                    <div class="bg-white dark:bg-gray-800 p-6 rounded-xl shadow card-hover text-center">
                        <div class="w-12 h-12 bg-primary/10 dark:bg-blue-400/10 rounded-full flex items-center justify-center mx-auto mb-4">
                            <i class="fa fa-camera text-primary dark:text-blue-400 text-xl"></i>
                        </div>
                        <h4 class="text-lg font-bold mb-2">内容创作</h4>
                        <p class="text-gray-600 dark:text-gray-400">视频、图解与新媒体运营</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section id="experience" class="py-20">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 animate-fade-in-scroll">
            <div class="text-center mb-16">
                <h2 class="text-3xl font-bold mb-3">实践经历</h2>
                <p class="text-gray-600 dark:text-gray-400">媒体与企业传播实践经验</p>
            </div>

            <div class="max-w-3xl mx-auto space-y-12">
                <div class="timeline-item pl-8 pb-12">
                    <h4 class="text-xl font-bold">中国新闻社</h4>
                    <p class="text-primary dark:text-blue-400 font-medium">新媒体记者 | 2024</p>
                    <ul class="mt-4 space-y-2 text-gray-600 dark:text-gray-400">
                        <li>春运三部曲系列报道</li>
                        <li>累计播放量超100万</li>
                        <li>两部作品获得好稿奖</li>
                    </ul>
                </div>
                <div class="timeline-item pl-8 pb-12">
                    <h4 class="text-xl font-bold">光明网</h4>
                    <p class="text-primary dark:text-blue-400 font-medium">理论编辑部助理编辑 | 2025</p>
                    <ul class="mt-4 space-y-2 text-gray-600 dark:text-gray-400">
                        <li>审校30余篇专家稿件</li>
                        <li>制作多期理论图解</li>
                        <li>参与大型融媒体活动筹备</li>
                    </ul>
                </div>
                <div class="timeline-item pl-8">
                    <h4 class="text-xl font-bold">快手科技</h4>
                    <p class="text-primary dark:text-blue-400 font-medium">企业社会责任专员实习生 | 2025</p>
                    <ul class="mt-4 space-y-2 text-gray-600 dark:text-gray-400">
                        <li>公益传播策划</li>
                        <li>中华慈善日活动</li>
                        <li>AI乡村课堂项目</li>
                        <li>媒体关系维护</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <section id="research" class="py-20 bg-neutral dark:bg-gray-900">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 animate-fade-in-scroll">
            <div class="text-center mb-16">
                <h2 class="text-3xl font-bold mb-3">研究与项目</h2>
                <p class="text-gray-600 dark:text-gray-400">学术成果与研究项目</p>
            </div>

            <div class="grid md:grid-cols-2 gap-8">
                <div class="bg-white dark:bg-gray-800 p-6 rounded-xl shadow card-hover">
                    <span class="text-sm text-primary dark:text-blue-400 font-medium">论文</span>
                    <h3 class="text-xl font-bold mt-2 mb-4">极端天气报道的原则、理念与方法</h3>
                    <p class="text-gray-600 dark:text-gray-400 mb-4">发表平台：《中国记者》</p>
                    <div class="flex flex-wrap gap-2">
                        <span class="px-3 py-1 bg-gray-100 dark:bg-gray-700 rounded-full text-sm">灾害传播</span>
                        <span class="px-3 py-1 bg-gray-100 dark:bg-gray-700 rounded-full text-sm">新闻伦理</span>
                        <span class="px-3 py-1 bg-gray-100 dark:bg-gray-700 rounded-full text-sm">风险传播</span>
                    </div>
                </div>

                <div class="bg-white dark:bg-gray-800 p-6 rounded-xl shadow card-hover">
                    <span class="text-sm text-primary dark:text-blue-400 font-medium">项目</span>
                    <h3 class="text-xl font-bold mt-2 mb-4">北京国企新媒体传播力蓝皮书（2025）</h3>
                    <h4 class="font-medium mb-2">职责：</h4>
                    <ul class="space-y-1 text-gray-600 dark:text-gray-400 mb-4">
                        <li>数据整理</li>
                        <li>指标分析</li>
                        <li>传播策略研究</li>
                    </ul>
                    <p class="text-gray-600 dark:text-gray-400"><strong>成果：</strong> 提出公众号运营体系优化建议</p>
                </div>
            </div>
        </div>
    </section>

    <section class="py-20">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 animate-fade-in-scroll">
            <div class="text-center mb-16">
                <h2 class="text-3xl font-bold mb-3">研究兴趣</h2>
                <p class="text-gray-600 dark:text-gray-400">关注的传播领域与研究方向</p>
            </div>

            <div class="flex flex-wrap justify-center gap-3 max-w-4xl mx-auto">
                <span class="px-4 py-2 bg-primary/10 dark:bg-blue-400/10 text-primary dark:text-blue-400 rounded-full text-lg font-medium">AI传播</span>
                <span class="px-4 py-2 bg-gray-100 dark:bg-gray-800 rounded-full text-lg font-medium">数字传播</span>
                <span class="px-4 py-2 bg-gray-100 dark:bg-gray-800 rounded-full text-lg font-medium">平台治理</span>
                <span class="px-4 py-2 bg-primary/10 dark:bg-blue-400/10 text-primary dark:text-blue-400 rounded-full text-lg font-medium">网络健康传播</span>
                <span class="px-4 py-2 bg-gray-100 dark:bg-gray-800 rounded-full text-lg font-medium">媒介社会学</span>
                <span class="px-4 py-2 bg-primary/10 dark:bg-blue-400/10 text-primary dark:text-blue-400 rounded-full text-lg font-medium">算法传播</span>
                <span class="px-4 py-2 bg-gray-100 dark:bg-gray-800 rounded-full text-lg font-medium">新闻生产研究</span>
                <span class="px-4 py-2 bg-gray-100 dark:bg-gray-800 rounded-full text-lg font-medium">风险传播</span>
                <span class="px-4 py-2 bg-gray-100 dark:bg-gray-800 rounded-full text-lg font-medium">内容运营</span>
                <span class="px-4 py-2 bg-primary/10 dark:bg-blue-400/10 text-primary dark:text-blue-400 rounded-full text-lg font-medium">新媒体传播</span>
            </div>
        </div>
    </section>

    <section id="portfolio" class="py-20 bg-neutral dark:bg-gray-900">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 animate-fade-in-scroll">
            <div class="text-center mb-16">
                <h2 class="text-3xl font-bold mb-3">作品集</h2>
                <p class="text-gray-600 dark:text-gray-400">新闻创作与传播实践成果</p>
            </div>

            <div class="flex flex-wrap justify-center gap-3 mb-10">
                <button class="filter-btn px-4 py-2 bg-primary dark:bg-blue-600 text-white rounded-lg">全部作品</button>
                <button class="filter-btn px-4 py-2 bg-white dark:bg-gray-800 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors">新闻报道</button>
                <button class="filter-btn px-4 py-2 bg-white dark:bg-gray-800 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors">短视频</button>
                <button class="filter-btn px-4 py-2 bg-white dark:bg-gray-800 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors">视觉设计</button>
                <button class="filter-btn px-4 py-2 bg-white dark:bg-gray-800 rounded-lg hover:bg-gray-100 dark:hover:bg-gray-700 transition-colors">传播策划</button>
            </div>

            <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6">
                <div class="bg-white dark:bg-gray-800 rounded-xl overflow-hidden shadow card-hover">
                    <div class="h-48 bg-gray-200 dark:bg-gray-700 flex items-center justify-center">
                        <i class="fa fa-video-camera text-4xl text-gray-400"></i>
                    </div>
                    <div class="p-5">
                        <h3 class="font-bold text-lg">春运三部曲系列报道</h3>
                        <p class="text-gray-600 dark:text-gray-400 text-sm mt-2">中国新闻社 | 百万播放作品</p>
                        <span class="inline-block mt-3 px-2 py-1 bg-blue-100 dark:bg-blue-900 text-blue-800 dark:text-blue-200 text-xs rounded">新闻报道</span>
                    </div>
                </div>
                <div class="bg-white dark:bg-gray-800 rounded-xl overflow-hidden shadow card-hover">
                    <div class="h-48 bg-gray-200 dark:bg-gray-700 flex items-center justify-center">
                        <i class="fa fa-image text-4xl text-gray-400"></i>
                    </div>
                    <div class="p-5">
                        <h3 class="font-bold text-lg">理论图解作品</h3>
                        <p class="text-gray-600 dark:text-gray-400 text-sm mt-2">光明网 | 理论传播可视化</p>
                        <span class="inline-block mt-3 px-2 py-1 bg-purple-100 dark:bg-purple-900 text-purple-800 dark:text-purple-200 text-xs rounded">视觉设计</span>
                    </div>
                </div>
                <div class="bg-white dark:bg-gray-800 rounded-xl overflow-hidden shadow card-hover">
                    <div class="h-48 bg-gray-200 dark:bg-gray-700 flex items-center justify-center">
                        <i class="fa fa-bullhorn text-4xl text-gray-400"></i>
                    </div>
                    <div class="p-5">
                        <h3 class="font-bold text-lg">AI乡村课堂项目</h3>
                        <p class="text-gray-600 dark:text-gray-400 text-sm mt-2">快手科技 | 公益传播</p>
                        <span class="inline-block mt-3 px-2 py-1 bg-green-100 dark:bg-green-900 text-green-800 dark:text-green-200 text-xs rounded">传播策划</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <section class="py-20">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 animate-fade-in-scroll">
            <div class="text-center mb-16">
                <h2 class="text-3xl font-bold mb-3">荣誉与资质</h2>
                <p class="text-gray-600 dark:text-gray-400">奖项与专业能力认证</p>
            </div>

            <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-6 gap-5">
                <div class="text-center p-4">
                    <div class="w-12 h-12 bg-primary/10 dark:bg-blue-400/10 rounded-full flex items-center justify-center mx-auto mb-3">
                        <i class="fa fa-trophy text-primary dark:text-blue-400"></i>
                    </div>
                    <p class="text-sm font-medium">国家奖学金</p>
                </div>
                <div class="text-center p-4">
                    <div class="w-12 h-12 bg-primary/10 dark:bg-blue-400/10 rounded-full flex items-center justify-center mx-auto mb-3">
                        <i class="fa fa-certificate text-primary dark:text-blue-400"></i>
                    </div>
                    <p class="text-sm font-medium">北京市优秀毕业生</p>
                </div>
                <div class="text-center p-4">
                    <div class="w-12 h-12 bg-primary/10 dark:bg-blue-400/10 rounded-full flex items-center justify-center mx-auto mb-3">
                        <i class="fa fa-users text-primary dark:text-blue-400"></i>
                    </div>
                    <p class="text-sm font-medium">优秀学生干部</p>
                </div>
                <div class="text-center p-4">
                    <div class="w-12 h-12 bg-primary/10 dark:bg-blue-400/10 rounded-full flex items-center justify-center mx-auto mb-3">
                        <i class="fa fa-flag text-primary dark:text-blue-400"></i>
                    </div>
                    <p class="text-sm font-medium">优秀共青团员</p>
                </div>
                <div class="text-center p-4">
                    <div class="w-12 h-12 bg-primary/10 dark:bg-blue-400/10 rounded-full flex items-center justify-center mx-auto mb-3">
                        <i class="fa fa-language text-primary dark:text-blue-400"></i>
                    </div>
                    <p class="text-sm font-medium">英语 CET-6</p>
                </div>
                <div class="text-center p-4">
                    <div class="w-12 h-12 bg-primary/10 dark:bg-blue-400/10 rounded-full flex items-center justify-center mx-auto mb-3">
                        <i class="fa fa-laptop text-primary dark:text-blue-400"></i>
                    </div>
                    <p class="text-sm font-medium">计算机二级</p>
                </div>
            </div>
        </div>
    </section>

    <section id="contact" class="py-20 bg-primary dark:bg-gray-900 text-white">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 animate-fade-in-scroll">
            <div class="text-center mb-16">
                <h2 class="text-3xl font-bold mb-3">联系我</h2>
                <p class="max-w-2xl mx-auto">欢迎交流新闻传播研究、新媒体运营与AI传播相关议题。</p>
            </div>

            <div class="grid md:grid-cols-2 gap-12">
                <div class="space-y-6">
                    <div class="flex items-center">
                        <div class="w-10 h-10 bg-white/10 rounded-full flex items-center justify-center mr-4">
                            <i class="fa fa-envelope"></i>
                        </div>
                        <div>
                            <h4 class="font-medium">邮箱</h4>
                            <p class="text-gray-300">your-email@example.com</p>
                        </div>
                    </div>
                    <div class="flex items-center">
                        <div class="w-10 h-10 bg-white/10 rounded-full flex items-center justify-center mr-4">
                            <i class="fa fa-phone"></i>
                        </div>
                        <div>
                            <h4 class="font-medium">电话</h4>
                            <p class="text-gray-300">your-phone-number</p>
                        </div>
                    </div>
                </div>
                <div class="grid grid-cols-3 gap-4">
                    <div class="bg-white/10 p-4 rounded-lg text-center hover:bg-white/20 transition-colors">
                        <i class="fa fa-weixin text-2xl mb-2"></i>
                        <p class="text-sm">微信</p>
                    </div>
                    <div class="bg-white/10 p-4 rounded-lg text-center hover:bg-white/20 transition-colors">
                        <i class="fa fa-github text-2xl mb-2"></i>
                        <p class="text-sm">GitHub</p>
                    </div>
                    <div class="bg-white/10 p-4 rounded-lg text-center hover:bg-white/20 transition-colors">
                        <i class="fa fa-wechat text-2xl mb-2"></i>
                        <p class="text-sm">公众号</p>
                    </div>
                    <div class="bg-white/10 p-4 rounded-lg text-center hover:bg-white/20 transition-colors">
                        <i class="fa fa-linkedin text-2xl mb-2"></i>
                        <p class="text-sm">LinkedIn</p>
                    </div>
                    <div class="bg-white/10 p-4 rounded-lg text-center hover:bg-white/20 transition-colors">
                        <i class="fa fa-file-text text-2xl mb-2"></i>
                        <p class="text-sm">简历</p>
                    </div>
                    <div class="bg-white/10 p-4 rounded-lg text-center hover:bg-white/20 transition-colors">
                        <i class="fa fa-graduation-cap text-2xl mb-2"></i>
                        <p class="text-sm">学术主页</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <footer class="py-8 bg-gray-100 dark:bg-gray-950 text-gray-600 dark:text-gray-400">
        <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
            <p>© 2025 张宇涵 | 新闻传播研究者</p>
            <p class="text-sm mt-2">News Communication · Digital Media · AI Communication</p>
        </div>
    </footer>

    <button id="backToTop" class="fixed bottom-6 right-6 w-12 h-12 bg-primary dark:bg-blue-600 text-white rounded-full shadow-lg flex items-center justify-center opacity-0 invisible transition-all duration-400 cubic-bezier(0.23, 1, 0.32, 1)">
        <i class="fa fa-arrow-up"></i>
    </button>

    <script>
        function throttle(func, limit) {
            let inThrottle;
            return function() {
                const args = arguments;
                const context = this;
                if (!inThrottle) {
                    func.apply(context, args);
                    inThrottle = true;
                    setTimeout(() => inThrottle = false, limit);
                }
            }
        }

        window.addEventListener('DOMContentLoaded', () => {
            setTimeout(() => {
                document.getElementById('loader').classList.add('opacity-0');
                setTimeout(() => {
                    document.getElementById('loader').style.display = 'none';
                }, 500);
            }, 1000);

            const themeToggle = document.getElementById('themeToggle');
            themeToggle.addEventListener('click', () => {
                document.documentElement.classList.toggle('dark');
                localStorage.setItem('theme', document.documentElement.classList.contains('dark') ? 'dark' : 'light');
            });

            if (localStorage.getItem('theme') === 'dark' || (!localStorage.getItem('theme') && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
                document.documentElement.classList.add('dark');
            }

            const backToTop = document.getElementById('backToTop');
            let lastScroll = 0;
            const nav = document.querySelector('nav');

            const handleScroll = throttle(() => {
                const currentScroll = window.scrollY;
                
                if (currentScroll > 300) {
                    backToTop.classList.remove('opacity-0', 'invisible');
                    backToTop.classList.add('opacity-100', 'visible');
                } else {
                    backToTop.classList.add('opacity-0', 'invisible');
                    backToTop.classList.remove('opacity-100', 'visible');
                }
                
                if (currentScroll <= 80) {
                    nav.style.transform = 'translateY(0)';
                } else if (currentScroll > lastScroll && currentScroll > 100) {
                    nav.style.transform = 'translateY(-100%)';
                } else {
                    nav.style.transform = 'translateY(0)';
                }
                lastScroll = currentScroll;
                
                const winScroll = document.body.scrollTop || document.documentElement.scrollTop;
                const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
                const scrolled = (winScroll / height) * 100;
                document.getElementById('progressBar').style.width = scrolled + '%';

                const scrollElements = document.querySelectorAll('.animate-fade-in-scroll');
                scrollElements.forEach(el => {
                    const rect = el.getBoundingClientRect();
                    const isVisible = rect.top < window.innerHeight - 120;
                    if (isVisible) el.classList.add('visible');
                });
            }, 15);

            window.addEventListener('scroll', handleScroll);
            handleScroll();

            backToTop.addEventListener('click', () => {
                window.scrollTo({ top: 0, behavior: 'smooth' });
            });

            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', e => {
                    e.preventDefault();
                    const target = document.querySelector(anchor.getAttribute('href'));
                    if (target) target.scrollIntoView({ behavior: 'smooth' });
                });
            });

            const filterBtns = document.querySelectorAll('.filter-btn');
            filterBtns.forEach(btn => {
                btn.addEventListener('click', () => {
                    filterBtns.forEach(b => {
                        b.classList.remove('bg-primary', 'dark:bg-blue-600', 'text-white');
                        b.classList.add('bg-white', 'dark:bg-gray-800');
                    });
                    btn.classList.remove('bg-white', 'dark:bg-gray-800');
                    btn.classList.add('bg-primary', 'dark:bg-blue-600', 'text-white');
                });
            });
        });
    </script>
</body>
</html>
