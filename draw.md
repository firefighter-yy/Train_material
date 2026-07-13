flowchart LR
    %% 样式定义
    classDef workspace fill:#E3F2FD,stroke:#1565C0,color:#1565C0,stroke-width:2px
    classDef staging fill:#FFF3E0,stroke:#E65100,color:#E65100,stroke-width:2px
    classDef localRepo fill:#F3E5F5,stroke:#6A1B9A,color:#6A1B9A,stroke-width:2px
    classDef remoteRepo fill:#E8F5E9,stroke:#2E7D32,color:#2E7D32,stroke-width:2px
    %% 同向箭头颜色定义
    linkStyle 0 stroke:#1565C0,stroke-width:2px   %% add → 蓝色
    linkStyle 1 stroke:#6A1B9A,stroke-width:2px   %% commit → 紫色
    linkStyle 2 stroke:#2E7D32,stroke-width:2px   %% push → 绿色
    linkStyle 3 stroke:#2E7D32,stroke-width:2px   %% fetch → 绿色
    linkStyle 4 stroke:#FF6F00,stroke-width:2px   %% pull → 橙色
    linkStyle 5 stroke:#6A1B9A,stroke-width:2px   %% reset → 紫色
    linkStyle 6 stroke:#1565C0,stroke-width:2px   %% restore → 蓝色
    subgraph Local["📁 本地仓库 Local"]
        WS["🏠 工作区<br/>Working Directory"]:::workspace
        SA["📋 暂存区<br/>Staging Area"]:::staging
        LR["📦 本地仓库<br/>Local Repository"]:::localRepo
    end
    RR["☁️ 远程仓库<br/>Remote Repository"]:::remoteRepo
    WS -- "git add" --> SA
    SA -- "git commit" --> LR
    LR -- "git push" --> RR
    RR -- "git fetch" --> LR
    RR -- "git pull" --> WS
    LR -- "git reset" --> SA
    SA -- "git restore --staged" --> WS