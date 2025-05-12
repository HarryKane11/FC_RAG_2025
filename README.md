# FC_RAG_2025
모두의 AI 케인의 Agent로 완성하는 RAG 강의 레포지토리입니다.

## 소개
"모두의 AI 케인의 Agent로 완성하는 RAG: 데이터 별 아키텍처 설계를 중심으로" 강의의 실습 자료입니다. 
이 강의에서는 2025년 LangGraph로 재편된 RAG 입문부터 구축 실습까지 다룹니다.
본 레포지토리를 git clone하시고 setup 가이드라인에 따라 환경을 구축하신 커널로 실행하시면 의존성 문제 없이 실습을 진행하실 수 있습니다.

## 주의사항
- **본 레포지토리는 교육 및 실습 목적으로만 사용해주세요.**
- **프로덕션 환경에서 사용을 권장하지 않습니다**: PyTorch, Transformers 등 패키지에 알려진 보안 취약점이 있을 수 있습니다.
- 본 레포지토리를 git clone하신 후 아래 설치 가이드라인에 따라 환경을 구축하시면 의존성 문제 없이 실습을 진행하실 수 있습니다.


<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Windows 환경에서 Docker 설치 가이드</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@fortawesome/fontawesome-free@6.0.0/css/all.min.css">
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            background-color: #f8f9fa;
        }
        
        pre {
            white-space: pre-wrap;
            word-wrap: break-word;
            padding: 1rem;
            background-color: #f1f1f1;
            border-radius: 0.375rem;
            font-family: Consolas, Monaco, 'Andale Mono', monospace;
            overflow-x: auto;
        }
        
        .code {
            background-color: #f1f1f1;
            padding: 0.2em 0.4em;
            border-radius: 3px;
            font-family: Consolas, Monaco, 'Andale Mono', monospace;
            font-size: 0.9em;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 2rem;
        }
        
        .warning {
            background-color: #fff3cd;
            color: #856404;
            padding: 1rem;
            margin: 1rem 0;
            border-left: 4px solid #ffeeba;
            border-radius: 0.25rem;
        }
        
        .tip {
            background-color: #d1ecf1;
            color: #0c5460;
            padding: 1rem;
            margin: 1rem 0;
            border-left: 4px solid #bee5eb;
            border-radius: 0.25rem;
        }
        
        .step {
            margin-bottom: 2rem;
            border-left: 3px solid #4299e1;
            padding-left: 1.5rem;
        }
        
        h1, h2, h3 {
            font-weight: 600;
        }
        
        h1 {
            font-size: 2.25rem;
            margin-bottom: 2rem;
            color: #2b6cb0;
        }
        
        h2 {
            font-size: 1.75rem;
            margin: 2rem 0 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 1px solid #e2e8f0;
            color: #2c5282;
        }
        
        h3 {
            font-size: 1.25rem;
            margin: 1.5rem 0 1rem;
            color: #2d3748;
        }
        
        img {
            max-width: 100%;
            height: auto;
            margin: 1rem 0;
            border: 1px solid #e2e8f0;
            border-radius: 0.375rem;
        }

        .command-box {
            background-color: #1a202c;
            color: #f7fafc;
            padding: 1rem;
            border-radius: 0.375rem;
            margin: 1rem 0;
            overflow-x: auto;
        }
        
        .command-box code {
            font-family: Consolas, Monaco, 'Andale Mono', monospace;
        }
        
        .table-of-contents {
            background-color: #ebf8ff;
            padding: 1.5rem;
            border-radius: 0.5rem;
            margin-bottom: 2rem;
        }
        
        .table-of-contents ul {
            list-style-type: none;
            padding-left: 0;
        }
        
        .table-of-contents ul li {
            margin-bottom: 0.5rem;
        }
        
        .table-of-contents a {
            color: #3182ce;
            text-decoration: none;
        }
        
        .table-of-contents a:hover {
            text-decoration: underline;
        }
        
        .numbered-step {
            display: flex;
            margin-bottom: 1rem;
        }
        
        .step-number {
            background-color: #4299e1;
            color: white;
            width: 28px;
            height: 28px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 1rem;
            flex-shrink: 0;
        }
        
        .step-content {
            flex: 1;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Windows 환경에서 Docker 설치 가이드</h1>
        
        <div class="table-of-contents">
            <h3 class="text-lg font-bold mb-3">목차</h3>
            <ul>
                <li><a href="#requirements">1. 시스템 요구사항 확인</a></li>
                <li><a href="#wsl">2. WSL 2 설치 및 구성</a></li>
                <li><a href="#docker-desktop">3. Docker Desktop 다운로드 및 설치</a></li>
                <li><a href="#optimization">4. Docker 설정 최적화</a></li>
                <li><a href="#testing">5. 기본 Docker 명령어 테스트</a></li>
                <li><a href="#qdrant">6. Qdrant Docker 이미지 실행방법</a></li>
                <li><a href="#troubleshooting">7. 문제 해결 가이드</a></li>
            </ul>
        </div>
        
        <section id="requirements">
            <h2>1. 시스템 요구사항 확인</h2>
            <p>Docker Desktop을 설치하기 전에 시스템이 다음 요구사항을 충족하는지 확인하세요.</p>
            
            <h3>최소 요구사항</h3>
            <ul class="list-disc ml-6 mb-4">
                <li>Windows 10 64-bit: Home, Pro, Enterprise, Education (버전 1903 이상)</li>
                <li>Windows 11 64-bit: Home, Pro, Enterprise, Education</li>
                <li>최소 4GB RAM (8GB 이상 권장)</li>
                <li>64비트 프로세서</li>
                <li>BIOS에서 하드웨어 가상화 지원 활성화 (Intel VT-x 또는 AMD-V)</li>
                <li>BIOS에서 Second Level Address Translation (SLAT) 지원</li>
                <li>WSL 2 설치 가능 상태</li>
            </ul>
            
            <h3>하드웨어 가상화 확인 방법</h3>
            <div class="step">
                <div class="numbered-step">
                    <div class="step-number">1</div>
                    <div class="step-content">
                        <p>작업 관리자를 열고 성능 탭으로 이동합니다.</p>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">2</div>
                    <div class="step-content">
                        <p>CPU 항목을 선택하고 '가상화'가 '사용'으로 표시되어 있는지 확인합니다.</p>
                    </div>
                </div>
            </div>
            
            <div class="warning">
                <p class="font-bold"><i class="fas fa-exclamation-triangle mr-2"></i>주의사항</p>
                <p>하드웨어 가상화가 비활성화되어 있다면, BIOS/UEFI 설정으로 들어가서 활성화해야 합니다. 이 과정은 컴퓨터 제조사 및 모델에 따라 다를 수 있습니다.</p>
            </div>
        </section>
        
        <section id="wsl">
            <h2>2. WSL 2 설치 및 구성</h2>
            <p>Docker Desktop은 Windows Subsystem for Linux 2 (WSL 2)를 사용하여 성능을 향상시킵니다. WSL 2를 설치하고 기본 버전으로 설정해야 합니다.</p>
            
            <h3>WSL 2 설치하기</h3>
            <div class="step">
                <div class="numbered-step">
                    <div class="step-number">1</div>
                    <div class="step-content">
                        <p>관리자 권한으로 PowerShell을 실행합니다.</p>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">2</div>
                    <div class="step-content">
                        <p>Windows 기능 사용/사용 안 함 작업을 위해 다음 명령어를 실행합니다:</p>
                        <div class="command-box">
                            <code>dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart</code>
                        </div>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">3</div>
                    <div class="step-content">
                        <p>가상 머신 플랫폼 기능을 활성화합니다:</p>
                        <div class="command-box">
                            <code>dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart</code>
                        </div>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">4</div>
                    <div class="step-content">
                        <p>컴퓨터를 재시작합니다.</p>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">5</div>
                    <div class="step-content">
                        <p>WSL 2 Linux 커널 업데이트 패키지를 다운로드하고 설치합니다:</p>
                        <p><a href="https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi" class="text-blue-600 hover:underline" target="_blank">WSL2 Linux 커널 업데이트 패키지</a></p>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">6</div>
                    <div class="step-content">
                        <p>WSL 2를 기본 버전으로 설정합니다:</p>
                        <div class="command-box">
                            <code>wsl --set-default-version 2</code>
                        </div>
                    </div>
                </div>
            </div>
            
            <h3>Linux 배포판 설치</h3>
            <div class="step">
                <p>Microsoft Store에서 원하는 Linux 배포판(예: Ubuntu)을 설치할 수 있습니다. 또는 PowerShell에서 직접 설치할 수도 있습니다:</p>
                <div class="command-box">
                    <code>wsl --install -d Ubuntu</code>
                </div>
                <p>이 명령어는 Ubuntu를 다운로드하고 설치합니다. 설치 후 사용자 이름과 비밀번호를 설정하라는 메시지가 표시됩니다.</p>
            </div>
            
            <div class="tip">
                <p class="font-bold"><i class="fas fa-lightbulb mr-2"></i>팁</p>
                <p>Windows 11 또는 Windows 10 최신 버전에서는 <code class="code">wsl --install</code> 명령어만으로 모든 필수 구성 요소와 함께 기본 Ubuntu 배포판이 설치됩니다.</p>
            </div>
        </section>
        
        <section id="docker-desktop">
            <h2>3. Docker Desktop 다운로드 및 설치</h2>
            <p>WSL 2가 성공적으로 설치되면 Docker Desktop을 다운로드하고 설치할 수 있습니다.</p>
            
            <div class="step">
                <div class="numbered-step">
                    <div class="step-number">1</div>
                    <div class="step-content">
                        <p>Docker Desktop 설치 파일을 다운로드합니다:</p>
                        <p><a href="https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe" class="text-blue-600 hover:underline" target="_blank">Docker Desktop 다운로드</a></p>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">2</div>
                    <div class="step-content">
                        <p>다운로드한 설치 파일을 더블 클릭하여 설치를 시작합니다.</p>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">3</div>
                    <div class="step-content">
                        <p>설치 옵션에서 다음 항목이 선택되어 있는지 확인합니다:</p>
                        <ul class="list-disc ml-6 mb-4">
                            <li>"WSL 2 기반 엔진 사용"</li>
                            <li>"바탕 화면에 Docker Desktop 아이콘 추가"</li>
                        </ul>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">4</div>
                    <div class="step-content">
                        <p>"확인" 버튼을 클릭하여 설치를 진행합니다.</p>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">5</div>
                    <div class="step-content">
                        <p>설치가 완료되면 "닫기" 버튼을 클릭합니다. Docker Desktop이 자동으로 시작됩니다.</p>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">6</div>
                    <div class="step-content">
                        <p>Docker 이용 약관에 동의하고 필요에 따라 설정을 구성합니다.</p>
                    </div>
                </div>
            </div>
            
            <div class="warning">
                <p class="font-bold"><i class="fas fa-exclamation-triangle mr-2"></i>주의사항</p>
                <p>설치 중 "WSL 2 설치가 불완전합니다" 오류가 발생하면, WSL 2 설치 단계를 다시 확인하고 컴퓨터를 재시작한 후 다시 시도하세요.</p>
            </div>
        </section>
        
        <section id="optimization">
            <h2>4. Docker 설정 최적화</h2>
            <p>Docker Desktop 성능을 최적화하기 위해 다음 설정을 구성할 수 있습니다.</p>
            
            <div class="step">
                <div class="numbered-step">
                    <div class="step-number">1</div>
                    <div class="step-content">
                        <p>Docker Desktop을 실행하고 오른쪽 상단의 설정 아이콘(⚙️)을 클릭합니다.</p>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">2</div>
                    <div class="step-content">
                        <p>리소스 탭에서 다음 설정을 조정합니다:</p>
                        <ul class="list-disc ml-6 mb-4">
                            <li>CPU: 사용 가능한 CPU 코어의 절반 이상 할당</li>
                            <li>메모리: 최소 4GB (작업 부하에 따라 조정)</li>
                            <li>스왑: 2GB 이상</li>
                            <li>디스크 이미지 크기: 최소 60GB</li>
                        </ul>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">3</div>
                    <div class="step-content">
                        <p>WSL 통합을 구성합니다 (Resources > WSL Integration):</p>
                        <ul class="list-disc ml-6 mb-4">
                            <li>"WSL 통합 사용" 확인</li>
                            <li>Docker를 사용할 Linux 배포판 선택 (설치한 Ubuntu 등)</li>
                        </ul>
                    </div>
                </div>
                <div class="numbered-step">
                    <div class="step-number">4</div>
                    <div class="step-content">
                        <p>설정이 완료되면 "Apply & Restart" 버튼을 클릭하여 변경 사항을 적용합니다.</p>
                    </div>
                </div>
            </div>
            
            <div class="tip">
                <p class="font-bold"><i class="fas fa-lightbulb mr-2"></i>팁</p>
                <p>시스템 성능에 따라 리소스 할당을 조정하세요. 더 많은 리소스를 할당할수록 Docker 컨테이너 성능이 향상되지만, 호스트 시스템의 가용 리소스는 감소합니다.</p>
            </div>
        </section>
        
        <section id="testing">
            <h2>5. 기본 Docker 명령어 테스트</h2>
            <p>Docker가 올바르게 설치되었는지 확인하기 위해 몇 가지 기본 명령어를 테스트해 보겠습니다.</p>
            
            <div class="step">
                <h3>터미널에서 Docker 테스트</h3>
                <p>PowerShell 또는 명령 프롬프트를 열고 다음 명령어를 실행합니다:</p>
                
                <p>Docker 버전 확인:</p>
                <div class="command-box">
                    <code>docker --version</code>
                </div>
                <p>예상 출력: <code class="code">Docker version 24.0.2, build cb74dfc</code> (버전은 다를 수 있음)</p>
                
                <p>Docker 시스템 정보 확인:</p>
                <div class="command-box">
                    <code>docker info</code>
                </div>
                
                <p>Hello World 컨테이너 실행:</p>
                <div class="command-box">
                    <code>docker run hello-world</code>
                </div>
                <p>이 명령어는 Docker Hub에서 hello-world 이미지를 다운로드하고 컨테이너를 실행합니다. 성공적으로 실행되면 환영 메시지가 표시됩니다.</p>
                
                <h3>WSL 2에서 Docker 테스트</h3>
                <p>WSL 2 터미널에서도 Docker 명령어가 작동하는지 확인해 보세요:</p>
                <ol class="list-decimal ml-6 mb-4">
                    <li>시작 메뉴에서 "Ubuntu"를 검색하여 WSL 터미널을 실행합니다.</li>
                    <li>다음 명령어를 실행합니다:</li>
                </ol>
                <div class="command-box">
                    <code>docker run -it ubuntu bash</code>
                </div>
                <p>이 명령어는 Ubuntu 컨테이너를 실행하고 bash 셸을 제공합니다. <code class="code">exit</code> 명령으로 컨테이너를 종료할 수 있습니다.</p>
            </div>
        </section>
        
        <section id="qdrant">
            <h2>6. Qdrant Docker 이미지 실행방법</h2>
            <p>이제 Docker가 올바르게、 설치되었으므로 Qdrant를 Docker 컨테이너로 실행해 보겠습니다.</p>
            
            <div class="step">
                <h3>기본 Qdrant 컨테이너 실행</h3>
                <p>다음 명령어로 Qdrant 컨테이너를 실행합니다:</p>
                <div class="command-box">
                    <code>docker run -p 6333:6333 -p 6334:6334 qdrant/qdrant</code>
                </div>
                <p>이 명령어는 Qdrant 이미지를 다운로드하고 6333, 6334 포트를 호스트에 매핑하여 컨테이너를 시작합니다.</p>
                
                <h3>데이터 지속성을 위한 볼륨 마운트</h3>
                <p>Qdrant 데이터를 호스트 시스템에 저장하려면 볼륨을 마운트합니다:</p>
                <div class="command-box">
                    <code>docker run -p 6333:6333 -p 6334:6334 -v qdrant_storage:/qdrant/storage qdrant/qdrant</code>
                </div>
                
                <h3>컨테이너 백그라운드에서 실행</h3>
                <p>Qdrant 컨테이너를 백그라운드에서 실행하려면:</p>
                <div class="command-box">
                    <code>docker run -d -p 6333:6333 -p 6334:6334 -v qdrant_storage:/qdrant/storage qdrant/qdrant</code>
                </div>
                
                <h3>Qdrant 컨테이너 설정 구성</h3>
                <p>사용자 정의 설정 파일로 Qdrant를 실행하려면:</p>
                <ol class="list-decimal ml-6 mb-4">
                    <li>로컬 시스템에 <code class="code">config.yaml</code> 파일을 생성합니다.</li>
                    <li>다음 명령어로 컨테이너를 실행합니다:</li>
                </ol>
                <div class="command-box">
                    <code>docker run -d -p 6333:6333 -p 6334:6334 -v $(pwd)/config.yaml:/qdrant/config/production.yaml -v qdrant_storage:/qdrant/storage qdrant/qdrant</code>
                </div>
                <p>PowerShell에서는 $(pwd) 대신 ${PWD}를 사용합니다:</p>
                <div class="command-box">
                    <code>docker run -d -p 6333:6333 -p 6334:6334 -v ${PWD}/config.yaml:/qdrant/config/production.yaml -v qdrant_storage:/qdrant/storage qdrant/qdrant</code>
                </div>
            </div>
            
            <h3>Qdrant 컨테이너 테스트</h3>
            <div class="step">
                <p>Qdrant가 제대로 실행되고 있는지 확인하려면 웹 브라우저에서 다음 URL로 접속합니다:</p>
                <p><a href="http://localhost:6333/dashboard" class="text-blue-600 hover:underline" target="_blank">http://localhost:6333/dashboard</a></p>
                <p>또는 API를 통해 상태를 확인할 수 있습니다:</p>
                <div class="command-box">
                    <code>curl http://localhost:6333/</code>
                </div>
                <p>예상 응답:</p>
                <pre>{
  "title": "Qdrant - Vector Search Engine",
  "version": "1.x.x"
}</pre>
            </div>
            
            <div class="tip">
                <p class="font-bold"><i class="fas fa-lightbulb mr-2"></i>팁</p>
                <p>컨테이너 ID를 확인하려면 <code class="code">docker ps</code> 명령어를 사용하세요. 컨테이너를 중지하려면 <code class="code">docker stop 컨테이너ID</code>를 실행합니다.</p>
            </div>
        </section>
        
        <section id="troubleshooting">
            <h2>7. 문제 해결 가이드</h2>
            <p>Docker 설치나 Qdrant 실행 중 발생할 수 있는 일반적인 문제와 해결 방법입니다.</p>
            
            <div class="step">
                <h3>Docker Desktop이 시작되지 않는 경우</h3>
                <ol class="list-decimal ml-6 mb-4">
                    <li>WSL 2가 올바르게 설치되어 있는지 확인합니다: <code class="code">wsl -l -v</code></li>
                    <li>하드웨어 가상화가 활성화되어 있는지 확인합니다.</li>
                    <li>Windows 업데이트가 최신 상태인지 확인합니다.</li>
                    <li>Docker Desktop을 재설치합니다.</li>
                </ol>
                
                <h3>WSL 2 오류 메시지가 표시되는 경우</h3>
                <ol class="list-decimal ml-6 mb-4">
                    <li>Linux 커널 업데이트 패키지를 다시 설치합니다.</li>
                    <li>다음 명령어로 WSL을 업데이트합니다: <code class="code">wsl --update</code></li>
                </ol>
                
                <h3>포트 충돌 문제</h3>
                <p>Qdrant 포트(6333, 6334)가 이미 사용 중인 경우:</p>
                <ol class="list-decimal ml-6 mb-4">
                    <li>사용 중인 포트를 확인합니다: <code class="code">netstat -ano | findstr 6333</code></li>
                    <li>다른 포트를 사용하여 Qdrant를 실행합니다: <code class="code">docker run -p 7333:6333 -p 7334:6334 qdrant/qdrant</code></li>
                </ol>
                
                <h3>Docker 컨테이너가 정상적으로 종료되지 않는 경우</h3>
                <ol class="list-decimal ml-6 mb-4">
                    <li>실행 중인 컨테이너 목록 확인: <code class="code">docker ps -a</code></li>
                    <li>강제 종료: <code class="code">docker rm -f 컨테이너ID</code></li>
                </ol>
                
                <h3>WSL 2 메모리 사용량이 높은 경우</h3>
                <p>WSL 2가 시스템 메모리를 너무 많이 사용하는 경우, 다음과 같이 메모리 제한을 설정할 수 있습니다:</p>
                <ol class="list-decimal ml-6 mb-4">
                    <li>사용자 홈 디렉토리에 <code class="code">.wslconfig</code> 파일을 생성합니다.</li>
                    <li>다음 내용을 추가합니다:</li>
                </ol>
                <pre>[wsl2]
memory=4GB
processors=2</pre>
                <li>WSL을 재시작합니다: <code class="code">wsl --shutdown</code></li>
                
                <h3>Docker 명령어가 작동하지 않는 경우</h3>
                <ol class="list-decimal ml-6 mb-4">
                    <li>Docker Desktop이 실행 중인지 확인합니다.</li>
                    <li>Docker 서비스를 재시작합니다: <code class="code">Restart-Service *docker*</code></li>
                    <li>시스템을 재부팅합니다.</li>
                </ol>
            </div>
            
            <div class="warning">
                <p class="font-bold"><i class="fas fa-exclamation-triangle mr-2"></i>중요</p>
                <p>문제 해결에 어려움을 겪는 경우 <a href="https://docs.docker.com/desktop/troubleshoot/overview/" class="text-blue-600 hover:underline" target="_blank">Docker 공식 문서</a>나 <a href="https://qdrant.tech/documentation/" class="text-blue-600 hover:underline" target="_blank">Qdrant 문서</a>를 참조하세요.</p>
            </div>
        </section>
        
        <section class="mt-10 pt-6 border-t border-gray-300">
            <h2>결론</h2>
            <p>이 가이드를 통해 Windows 환경에서 Docker를 설치하고 Qdrant 벡터 데이터베이스를 실행하는 방법을 배웠습니다. 이제 Qdrant와 LangChain을 연계한 실습을 진행할 준비가 되었습니다.</p>
            <p>Docker와 Qdrant를 사용하여 벡터 검색, 유사성 검색, 메타데이터 필터링 등 다양한 기능을 탐색해 보세요.</p>
            <p class="mt-4">추가 질문이나 문제가 있으면 다음 리소스를 참조하세요:</p>
            <ul class="list-disc ml-6 mb-4">
                <li><a href="https://qdrant.tech/documentation/" class="text-blue-600 hover:underline" target="_blank">Qdrant 공식 문서</a></li>
                <li><a href="https://docs.docker.com/desktop/windows/wsl/" class="text-blue-600 hover:underline" target="_blank">Docker Desktop WSL 2 백엔드</a></li>
                <li><a href="https://learn.microsoft.com/ko-kr/windows/wsl/install" class="text-blue-600 hover:underline" target="_blank">Windows Subsystem for Linux 설치 가이드</a></li>
            </ul>
        </section>
    </div>
</body>
</html>
