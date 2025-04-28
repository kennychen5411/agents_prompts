``` mermaid
flowchart LR
    %% ──────────────── Host 端 ────────────────
    subgraph Host["Host 應用（IDE、桌面／Web App…）"]
        direction TB
        SDK[<font color="#4285F4"><u>Client SDK<br/>（TypeScript／Python／Java…）</u></font>]
        Client[<font color="#4285F4"><u>MCP Client<br/>（1 : 1 Session）</u></font>]
        SDK --> Client
    end

    %% ─────────── 註冊／市集 (Registry) ───────────
    Registry[<font color="#4285F4"><u>Registry／Market<br/>（MCP Market／Hub）</u></font>]

    %% ────────────── 傳輸層／Proxy ──────────────
    Proxy[<font color="#4285F4"><u>Proxy／Adapter<br/>（Stdio、HTTP-SSE、mcp-remote）</u></font>]

    %% ──────────────── Server 端開發輔助 ────────────────
    Framework[<font color="#4285F4"><u>Server-building Frameworks<br/>（提供結構、工具、樣板）</u></font>]

    %% ──────────────── Server 端 ────────────────
    subgraph ServerSide["MCP Server 執行實例"]
        Server[<font color="#4285F4"><u>MCP Server<br/>（包含由框架建構的 Tools、Resources、Prompts）</u></font>]
    end

    %% ─────────────── 關係箭頭 (修正標籤) ───────────────
    Client    -- "連線 & 能力協商" --> Proxy
    Proxy     -- "轉送 JSON-RPC"   --> Server
    Server    -- "註冊／發布"        --> Registry
    Client    -- "索引／發現"        --> Registry
    Framework -- "用於建構／實作 (開發階段)" --> Server

    %% 可並存多個 Host，示意
    subgraph "其他 Host"
        direction TB
        SDK2[Client SDK]
        Client2[MCP Client]
        SDK2 --> Client2
    end
    Client2 -- "連線" --> Proxy

    %% 節點樣式 (範例，未啟用)
    %%style Framework fill:#f9d7ae,stroke:#b8540d,stroke-width:2px

    %% --- 點擊連結定義 (保持不變) ---
    click Client "https://hackmd.io/fTuyxkDYT1qq_29cAGHVVw?view#1-%C2%B7-Hosts--Clients-top-10" "查看 Hosts & Clients 相關資訊" _blank
    click SDK "https://hackmd.io/fTuyxkDYT1qq_29cAGHVVw?view#2-%C2%B7-Client-SDKs-top-10" "查看 Client SDKs 相關資訊" _blank
    click Proxy "https://hackmd.io/fTuyxkDYT1qq_29cAGHVVw?view#3-%C2%B7-Proxy--Adapter-Utilities-top-10" "查看 Proxy/Adapter 相關資訊" _blank
    click Framework "https://hackmd.io/fTuyxkDYT1qq_29cAGHVVw?view#4-%C2%B7-Server-building-Frameworks-top-10" "查看 Server-building Frameworks 相關資訊" _blank
    click Server "https://hackmd.io/fTuyxkDYT1qq_29cAGHVVw?view#5-%C2%B7-Popular-MCP-Servers-tool-providers-top-10" "查看 MCP Servers / Tool Providers 相關資訊" _blank
    click Registry "https://hackmd.io/fTuyxkDYT1qq_29cAGHVVw?view#6-%C2%B7-Registries--Marketplaces-top-10" "查看 Registries/Marketplaces 相關資訊" _blank
    
```
