# 내 프로필을 클라우드에!

## 👨🏻‍💻프로젝트 간단요약

프로필 웹페이지를 AWS S3의 정적 웹 호스팅 기능을 활용하여 배포한다.

- 서비스 시연영상
    
    https://drive.google.com/file/d/1OmAZWIfnzAhOO8aObmUSjLGKkhJLrZxu/view?usp=drive_link
    

---

## 🙋🏻나는 무엇을 했는가?

- 프로젝트 일지
    
    [프로필 페이지 제작](https://www.notion.so/15ff514d0f084e0ab201eb01814f0a4d?pvs=21)
    

1. html 웹페이지 제작하였습니다.
    - 메인페이지코드
        
        ```python
        <!DOCTYPE html>
        <html lang="en">
            <head>
                <meta charset="utf-8" />
                <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
                <meta name="description" content="" />
                <meta name="author" content="" />
                <title>Profile</title>
                <!-- Favicon-->
                <link rel="icon" type="image/x-icon" href="assets/favicon.ico" />
                <!-- Custom Google font-->
                <link rel="preconnect" href="https://fonts.googleapis.com" />
                <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
                <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@100;200;300;400;500;600;700;800;900&amp;display=swap" rel="stylesheet" />
                <!-- Bootstrap icons-->
                <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.1/font/bootstrap-icons.css" rel="stylesheet" />
                <!-- Core theme CSS (includes Bootstrap)-->
                <link href="css/styles.css" rel="stylesheet" />
        
                
        
                  <!-- (이전 헤더 내용은 그대로 유지) -->
            
                
            </head>
            <body class="d-flex flex-column h-100">
                <main class="flex-shrink-0">
                    <!-- Navigation-->
                    <nav class="navbar navbar-expand-lg navbar-light bg-white py-3">
                        <div class="container-fluid px-5 right-0px"> <!-- container-fluid로 변경 -->
                            <a class="navbar-brand" href="index.html"><span class="fw-bolder text-primary">Profile</span></a>
                            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                                <span class="navbar-toggler-icon"></span>
                            </button>
                            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                                <ul class="navbar-nav ms-auto mb-2 mb-lg-0 small fw-bolder">
                                    <li class="nav-item"><a class="nav-link" href="index.html">Home</a></li>
                                    <li class="nav-item"><a class="nav-link" href="resume.html">Resume</a></li>
                                    <li class="nav-item"><a class="nav-link" href="projects.html">Projects</a></li>
                                    <!-- <li class="nav-item"><a class="nav-link" href="contact.html">Contact</a></li> -->
                                </ul>
                            </div>
                        </div>
                    </nav>
        
                    <!-- Header-->
                    <header class="py-5">
                        <div class="container" id="imageContainer">
                            <div class="overlay"></div>
                            <div class="card"></div>
                        </div>
                        <script>
                            var container = document.getElementById('imageContainer');
                            var overlay = container.querySelector('.overlay');
                        
                            container.addEventListener('mousemove', function (e) {
                                var x = e.offsetX;
                                var y = e.offsetY;
                                var rotateY = -1 / 5 * x + 20;
                                var rotateX = 4 / 30 * y - 20;
                        
                                overlay.style = `background-position : ${x / 5 + y / 5}%; filter : opacity(${x / 200}) brightness(1.2)`;
                                container.style = `transform : perspective(350px) rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
                                overlay.style.opacity = 1;
                            });
                        
                            container.addEventListener('mouseout', function () {
                                overlay.style = 'filter : opacity(0)';
                                container.style = 'transform : perspective(350px) rotateY(0deg) rotateX(0deg)';
                                overlay.style.opacity = 0;
                            });
                        </script>
                        <style>
                            @keyframes initialMoveImage {
                                0% {
                                    transform: translateZ(0) rotateX(0deg) rotateY(0deg);
                                    opacity: 0;
                                }
                                100% {
                                    transform: translateZ(0) rotateX(0deg) rotateY(0deg);
                                    opacity: 1;
                                }
                            }
                            .container {
                                width: 220px;
                                height: 310px;
                                transition: all 0.1s;
                                perspective: 1000px;
                                position: absolute;
                                right:70px;
                                animation: moveImage 1s;
                            }
                
                            .overlay {
                                position: absolute;
                                width: 100%;
                                height: 100%;
                                background: linear-gradient(105deg,
                                    transparent 40%,
                                    rgba(255, 219, 112, 0.8) 45%,
                                    rgba(132, 50, 255, 0.6) 50%,
                                    transparent 54%);
                                filter: brightness(1.1) opacity(0.8);
                                mix-blend-mode: color-dodge;
                                background-size: 150% 150%;
                                background-position: -20%;
                                transition: all 0.1s;
                                /* z-index: 1; */
                                right: 60px;
                                opacity: 0;
                            }
                
                            .card {
                                width: 220px;
                                height: 310px;
                                background-image: url('https://s3.ap-northeast-2.amazonaws.com/itmnm.link/assets/profilepic.jpg');
                                background-size: cover;
                                margin-left: right;
                                z-index: -1;
                                right: 70px;
                                }
                        </style>
        
                    </header>
        
                        
                        <div class="left-0 px-5 pb-5">
                            <div class="row gx-5 align-items-center">
                                <div class="col-xxl-5">
                                    <!-- Header text content-->
                                    <div class="text-center text-xxl-start">
                                        <div class="badge bg-gradient-primary-to-secondary text-white mb-4"><div class="text-uppercase">Cloud &middot; Solution &middot; Architect</div></div>
                                        <div class="fs-3 fw-light text-muted">Welcome to my profile</div>
                                        <h1 class="display-3 fw-bolder mb-5"><span class="text-gradient d-inline">Let's get started</span></h1>
                                        <div class="d-grid gap-3 d-sm-flex justify-content-sm-center justify-content-xxl-start mb-3">
                                            <a class="btn btn-primary btn-lg px-5 py-3 me-sm-3 fs-6 fw-bolder" href="resume.html">Resume</a>
                                            <a class="btn btn-outline-dark btn-lg px-5 py-3 fs-6 fw-bolder" href="projects.html">Projects</a>
                                        </div>
                                    </div>
                                </div>
                                <div class="col-xxl-7">
                                    <!-- Header profile picture-->
                                    <div class="d-flex justify-content-center mt-5 mt-xxl-0"> 
        
                                    </div>
                                </div>
                            </div>
                        </div>
                    <!-- About Section-->
                    <section class="bg-light py-5">
                        <div class="left-0 px-5">
                            <div class="row gx-5 justify-content-center">
                                <div class="col-xxl-8">
                                    <div class="text-center my-5">
                                        <h2 class="display-5 fw-bolder"><span class="text-gradient d-inline">About Me</span></h2>
                                        <p class="lead fw-light mb-4">MyeongHyeon Kim/noble3769@gmail.com</p>
                                        <p class="text-muted">More Info.</p>
                                        <div class="d-flex justify-content-center fs-2 gap-4">
                                            <!-- <a class="text-gradient" href="#!"><i class="bi bi-twitter"></i></a> -->
                                            
                                            <a class="text-gradient" href="https://github.com/it-mnm"><i class="bi bi-github"></i></a>
                                            <a class="text-gradient" href="https://itfragile.tistory.com/"><i class="bi bi-window"></i></a>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </section>
        
                </main>
        
                <!-- Footer-->
                <footer class="bg-white py-4 mt-auto">
                    <div class="container px-5">
                        <div class="row align-items-center justify-content-between flex-column flex-sm-row">
                            <div class="col-auto"><div class="small m-0">Copyright &copy; itmnm 2023</div></div>
                            <!-- <div class="col-auto">
                                <a class="small" href="#!">Privacy</a>
                                <span class="mx-1">&middot;</span>
                                <a class="small" href="#!">Terms</a>
                                <span class="mx-1">&middot;</span>
                                <a class="small" href="#!">Contact</a>
                            </div> -->
                        </div>
                    </div>
                </footer>
                
                <!-- Bootstrap core JS-->
                <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"></script>
                <!-- Core theme JS-->
                <script src="js/scripts.js"></script>
            </body>
        </html>
        ```
        
    - resume 페이지 코드
        
        ```python
        <!DOCTYPE html>
        <html lang="en">
            <head>
                <meta charset="utf-8" />
                <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
                <meta name="description" content="" />
                <meta name="author" content="" />
                <title>Profile</title>
                <!-- Favicon-->
                <link rel="icon" type="image/x-icon" href="assets/favicon.ico" />
                <!-- Custom Google font-->
                <link rel="preconnect" href="https://fonts.googleapis.com" />
                <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
                <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@100;200;300;400;500;600;700;800;900&amp;display=swap" rel="stylesheet" />
                <!-- Bootstrap icons-->
                <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.1/font/bootstrap-icons.css" rel="stylesheet" />
                <!-- Core theme CSS (includes Bootstrap)-->
                <link href="css/styles.css" rel="stylesheet" />
            </head>
            <body class="d-flex flex-column h-100 bg-light">
                <main class="flex-shrink-0">
                    <!-- Navigation-->
                    <nav class="navbar navbar-expand-lg navbar-light bg-white py-3">
                        <div class="container px-5">
                            <a class="navbar-brand" href="index.html"><span class="fw-bolder text-primary">Profile</span></a>
                            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation"><span class="navbar-toggler-icon"></span></button>
                            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                                <ul class="navbar-nav ms-auto mb-2 mb-lg-0 small fw-bolder">
                                    <li class="nav-item"><a class="nav-link" href="index.html">Home</a></li>
                                    <li class="nav-item"><a class="nav-link" href="resume.html">Resume</a></li>
                                    <li class="nav-item"><a class="nav-link" href="projects.html">Projects</a></li>
                                    <!-- <li class="nav-item"><a class="nav-link" href="contact.html">Contact</a></li> -->
                                </ul>
                            </div>
                        </div>
                    </nav>
                    <!-- Page Content-->
                    <div class="container px-5 my-5">
                        <div class="text-center mb-5">
                            <h1 class="display-5 fw-bolder mb-0"><span class="text-gradient d-inline">Resume</span></h1>
                        </div>
                        <div class="row gx-5 justify-content-center">
                            <div class="col-lg-11 col-xl-9 col-xxl-8">
                                <!-- Experience Section-->
                                <section>
                                    <div class="d-flex align-items-center justify-content-between mb-4">
                                        <h2 class="text-primary fw-bolder mb-0">Education</h2>
                                        <!-- Download resume button-->
                                        <!-- Note: Set the link href target to a PDF file within your project-->
                                        <!-- <a class="btn btn-primary px-4 py-3" href="#!">
                                            <div class="d-inline-block bi bi-download me-2"></div>
                                            Download Resume
                                        </a> -->
                                    </div>
                                    <!-- Experience Card 1-->
                                    <div class="card shadow border-0 rounded-4 mb-5">
                                        <div class="card-body p-5">
                                            <div class="row align-items-center gx-5">
                                                <div class="col text-center text-lg-start mb-4 mb-lg-0">
                                                    <div class="bg-light p-4 rounded-4">
                                                        <div class="text-primary fw-bolder mb-2">2018 - Present</div>
                                                        <div class="small fw-bolder">Kyonggi Univ.</div>
                                                        <div class="small text-muted">Student</div>
                                                    </div>
                                                </div>
                                                <div class="col-lg-8"><div>I majored in mechanical engineering and worked for 1 year and 6 months in a mechatronics research lab. I have experience in designing a small smart factory while gaining knowledge about automation systems, including Arduino.</div></div>
                                            </div>
                                        </div>
                                    </div>
                                    <!-- Experience Card 2-->
                                    <div class="card shadow border-0 rounded-4 mb-5">
                                        <div class="card-body p-5">
                                            <div class="row align-items-center gx-5">
                                                <div class="col text-center text-lg-start mb-4 mb-lg-0">
                                                    <div class="bg-light p-4 rounded-4">
                                                        <div class="text-primary fw-bolder mb-2">2023.06 - Present</div>
                                                        <div class="small fw-bolder">LG HelloVision DX DataSchool</div>
                                                        <div class="small text-muted">Student</div>
                                     
                                                    </div>
                                                </div>
                                                <div class="col-lg-8"><div>I developed my basic coding skills at Data School and learned data analysis, deep learning, and machine learning. Currently, I am learning about cloud and DevOps.</div></div>
                                            </div>
                                        </div>
                                    </div>
                                </section>
                                <!-- Education Section-->
        
                                <!-- Divider-->
                                <div class="pb-5"></div>
                                <!-- Skills Section-->
                                <section>
                                    <!-- Skillset Card-->
                                    <div class="card shadow border-0 rounded-4 mb-5">
                                        <div class="card-body p-5">
                                            <!-- Professional skills list-->
                                            <div class="mb-5">
                                                <div class="d-flex align-items-center mb-4">
                                                    <div class="feature bg-primary bg-gradient-primary-to-secondary text-white rounded-3 me-3"><i class="bi bi-tools"></i></div>
                                                    <h3 class="fw-bolder mb-0"><span class="text-gradient d-inline">Skills</span></h3>
                                                </div>
                                                <div class="row row-cols-1 row-cols-md-3 mb-4">
                                                    <div class="col mb-4 md-0" style="width: 240px; height: 15px; text-align: center;"><div class="d-flex align-items-center bg-light rounded-4 p-3 h-100">git</div></div>
                                                    <div class="col mb-4 md-0" style="width: 240px; height: 15px; text-align: center;"><div class="d-flex align-items-center bg-light rounded-4 p-3 h-100">Network</div></div>
                                                    <div class="col" style="width: 240px; height: 15px; text-align: center;"><div class="d-flex align-items-center bg-light rounded-4 p-3 h-100">AWS</div></div>
                                                </div>
                                                <div class="row row-cols-1 row-cols-md-3 mb-4">
                                                    <div class="col mb-4 mb-md-0" style="width: 240px; height: 15px; text-align: center mt-1;"><div class="d-flex align-items-center bg-light rounded-4 p-3 h-100">Airflow</div></div>
                                                    <div class="col mb-4 mb-md-0" style="width: 240px; height: 15px; text-align: center mt-1 ;"><div class="d-flex align-items-center bg-light rounded-4 p-3 h-100">Data Analytics</div></div>
                                                    <div class="col" style="width: 240px; height: 15px; text-align: center mt-1;"><div class="d-flex align-items-center bg-light rounded-4 p-3 h-100">Docker/k8s</div></div>
                                                </div>
                                            </div>
                                            <!-- Languages list-->
                                            <div class="mb-0">
                                                <div class="d-flex align-items-center mb-4">
                                                    <div class="feature bg-primary bg-gradient-primary-to-secondary text-white rounded-3 me-3"><i class="bi bi-code-slash"></i></div>
                                                    <h3 class="fw-bolder mb-0"><span class="text-gradient d-inline">Languages</span></h3>
                                                </div>
                                                <div class="row row-cols-1 row-cols-md-3 mb-4">
                                                    <div class="col mb-4 mb-md-0" style="width: 240px; height: 15px; text-align: center;"><div class="d-flex align-items-center bg-light rounded-4 p-3 h-100">HTML</div></div>
                                                    <div class="col mb-4 mb-md-0" style="width: 240px; height: 15px; text-align: center;"><div class="d-flex align-items-center bg-light rounded-4 p-3 h-100">CSS</div></div>
                                                    <div class="col" style="width: 240px; height: 15px; text-align: center;"><div class="d-flex align-items-center bg-light rounded-4 p-3 h-100">Python</div></div>
                                                </div>
        
                                            </div>
                                        </div>
                                    </div>
                                </section>
                            </div>
                        </div>
                    </div>
                </main>
                <!-- Footer-->
                <footer class="bg-white py-4 mt-auto">
                    <div class="container px-5">
                        <div class="row align-items-center justify-content-between flex-column flex-sm-row">
                            <div class="col-auto"><div class="small m-0">Copyright &copy; itmnm 2023</div></div>
                            <!-- <div class="col-auto">
                                <a class="small" href="#!">Privacy</a>
                                <span class="mx-1">&middot;</span>
                                <a class="small" href="#!">Terms</a>
                                <span class="mx-1">&middot;</span>
                                <a class="small" href="#!">Contact</a>
                            </div> -->
                        </div>
                    </div>
                </footer>
                <!-- Bootstrap core JS-->
                <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"></script>
                <!-- Core theme JS-->
                <script src="js/scripts.js"></script>
            </body>
        </html>
        ```
        
    - projects 페이지 코드
        
        ```python
        <!DOCTYPE html>
        <html lang="en">
            <head>
                <meta charset="utf-8" />
                <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no" />
                <meta name="description" content="" />
                <meta name="author" content="" />
                <title>Profile</title>
                <!-- Favicon-->
                <link rel="icon" type="image/x-icon" href="assets/favicon.ico" />
                <!-- Custom Google font-->
                <link rel="preconnect" href="https://fonts.googleapis.com" />
                <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
                <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@100;200;300;400;500;600;700;800;900&amp;display=swap" rel="stylesheet" />
                <!-- Bootstrap icons-->
                <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.8.1/font/bootstrap-icons.css" rel="stylesheet" />
                <!-- Core theme CSS (includes Bootstrap)-->
                <link href="css/styles.css" rel="stylesheet" />
            </head>
            <body class="d-flex flex-column h-100 bg-light">
                <main class="flex-shrink-0">
                    <!-- Navigation-->
                    <nav class="navbar navbar-expand-lg navbar-light bg-white py-3">
                        <div class="container px-5">
                            <a class="navbar-brand" href="index.html"><span class="fw-bolder text-primary">Profile</span></a>
                            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation"><span class="navbar-toggler-icon"></span></button>
                            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                                <ul class="navbar-nav ms-auto mb-2 mb-lg-0 small fw-bolder">
                                    <li class="nav-item"><a class="nav-link" href="index.html">Home</a></li>
                                    <li class="nav-item"><a class="nav-link" href="resume.html">Resume</a></li>
                                    <li class="nav-item"><a class="nav-link" href="projects.html">Projects</a></li>
                                    <!-- <li class="nav-item"><a class="nav-link" href="contact.html">Contact</a></li> -->
                                </ul>
                            </div>
                        </div>
                    </nav>
                    <!-- Projects Section-->
                    <section class="py-5">
                        <div class="container px-5 mb-5">
                            <div class="text-center mb-5">
                                <h1 class="display-5 fw-bolder mb-0"><span class="text-gradient d-inline">Projects</span></h1>
                            </div>
                            <div class="row gx-5 justify-content-center">
                                <div class="col-lg-11 col-xl-9 col-xxl-8">
                                    <!-- Project Card 1-->
                                    <div class="card overflow-hidden shadow rounded-4 border-0 mb-5">
                                        <div class="card-body p-0 mt-3 mb-3">
                                            <div class="d-flex align-items-center">
                                                <!-- <div class="p-5">
                                                    <h2 class="fw-bolder">Project 1</h2>
                                                    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Eius at enim eum illum aperiam placeat esse? Mollitia omnis minima saepe recusandae libero, iste ad asperiores! Explicabo commodi quo itaque! Ipsam!</p>
                                                </div> -->
                                                <img class="img-fluid" src="https://s3.ap-northeast-2.amazonaws.com/itmnm.link/assets/architect.webp" alt="..." />
                                            </div>
                                        </div>
                                    </div>
        
                                    <!-- Project Card 2-->
                                    <div class="card overflow-hidden shadow rounded-4 mb-5 border-0">
                                        <div class="card-body p-0 mt-3">
                                            <div class="d-flex align-items-center">
                                                <!-- <div class="p-5">
                                                    <h2 class="fw-bolder">Project 2</h2>
                                                    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Eius at enim eum illum aperiam placeat esse? Mollitia omnis minima saepe recusandae libero, iste ad asperiores! Explicabo commodi quo itaque! Ipsam!</p>
                                                </div> -->
                                                <img class="img-fluid" src="https://s3.ap-northeast-2.amazonaws.com/itmnm.link/assets/1_zWF66mV-bUbvBKvvZxVIiw.png" alt="..." />
                                            </div>
                                        </div>
                                    </div>
                                    
                                    <!-- Project Card 3-->
                                    <div class="card overflow-hidden shadow rounded-4 border-0 mb-5">
                                        <div class="card-body p-0">
                                            <div class="d-flex align-items-center">
                                                <!-- <div class="p-5">
                                                    <h2 class="fw-bolder">Project 1</h2>
                                                    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Eius at enim eum illum aperiam placeat esse? Mollitia omnis minima saepe recusandae libero, iste ad asperiores! Explicabo commodi quo itaque! Ipsam!</p>
                                                </div> -->
                                                <img class="img-fluid" src="https://s3.ap-northeast-2.amazonaws.com/itmnm.link/assets/vod architecture.png" alt="..." />
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </section>
                    <!-- Call to action section-->
                    <section class="py-5 bg-gradient-primary-to-secondary text-white">
                        <div class="container px-5 my-5">
                            <div class="text-center">
                                <!-- <h2 class="display-4 fw-bolder mb-4">Let's build something together</h2> -->
                                <!-- <a class="btn btn-outline-light btn-lg px-5 py-3 fs-6 fw-bolder" href="contact.html">Contact me</a> -->
                            </div>
                        </div>
                    </section>
                </main>
                <!-- Footer-->
                <footer class="bg-white py-4 mt-auto">
                    <div class="container px-5">
                        <div class="row align-items-center justify-content-between flex-column flex-sm-row">
                            <div class="col-auto"><div class="small m-0">Copyright &copy; itmnm 2023</div></div>
                            <!-- <div class="col-auto">
                                <a class="small" href="#!">Privacy</a>
                                <span class="mx-1">&middot;</span>
                                <a class="small" href="#!">Terms</a>
                                <span class="mx-1">&middot;</span>
                                 <a class="small" href="#!">Contact</a>
                            </div> -->
                        </div>
                    </div>
                </footer>
                <!-- Bootstrap core JS-->
                <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"></script>
                <!-- Core theme JS-->
                <script src="js/scripts.js"></script>
            </body>
        </html>
        ```
        
    
2. AWS 환경에서 정적 웹을 배포하였습니다.
    - Architecture
        
        ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/df3849f7-f233-4fe8-88e6-7e7528b6fb56/053717f5-036c-4ec3-8a26-1835da8b19b8/Untitled.png)
        
    - 배포된 사진
        - S3(React 웹)
            
            ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/df3849f7-f233-4fe8-88e6-7e7528b6fb56/91120eaa-db89-49aa-bed3-ac7b96d26a8f/Untitled.png)
            
        
    

---

## 📖나는 무엇을 배웠는가?

1. S3는 단순히 저장소 역할을 하는 것을 넘어서 **정적 웹을 호스팅 할 수 있다는 것을 알았다.** 
2. 보안을 위해 https 통신을 하도록 만들었는데, 이를 위해서는 보안 인증서가 필요하다. AWS에서는 클라이언트의 https 통신을 이루기 위해서는 **반드시 인증서를 버지니아 북부에 위치시켜야한다.** 또한 CloudFront를 이용하여 그 인증서를 국내에서 빠르게 이용할 수 있도록 만들어야 한다.

---

## ➕앞으로 무엇을 더 보완할 수 있는가?

1. 코드가 수정되었을때 일일히 손으로 S3에 옮겨서 배포하는 것은 매우 불편한 과정이다. 따라서 git action 등을 통해 **자동 배포를 구현하는 것이 좋을 듯 하다.**
2. 정적 웹 호스팅이 완료되었으니, 백엔드 서버를 연결해보거나, 시각화도구(ex - Tableau)를 웹에 띄워보는 것도 해볼 수 있을 것이다.
3. 추후에 NFS를 이용하는 파일관리와 S3를 이용하여 하는 파일관리의 **속도차이를 비교해보고싶다.**
