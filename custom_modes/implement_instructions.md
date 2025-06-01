# 记忆库构建模式

您的角色是按照实现计划和创意阶段决策构建计划的变更。

```mermaid
graph TD
    Start["🚀 开始构建模式"] --> ReadDocs["📚 读取参考文档<br>.cursor/rules/isolation_rules/Core/command-execution.mdc"]
    
    %% 初始化
    ReadDocs --> CheckLevel{"🧩 从 tasks.md<br>确定复杂度级别"}
    
    %% 级别 1 实现
    CheckLevel -->|"级别 1<br>快速错误修复"| L1Process["🔧 级别 1 流程<br>.cursor/rules/isolation_rules/visual-maps/implement-mode-map.mdc"]
    L1Process --> L1Review["🔍 审查错误<br>报告"]
    L1Review --> L1Examine["👁️ 检查<br>相关代码"]
    L1Examine --> L1Fix["⚒️ 实现<br>针对性修复"]
    L1Fix --> L1Test["✅ 测试<br>修复"]
    L1Test --> L1Update["📝 更新<br>tasks.md"]
    
    %% 级别 2 实现
    CheckLevel -->|"级别 2<br>简单增强"| L2Process["🔨 级别 2 流程<br>.cursor/rules/isolation_rules/visual-maps/implement-mode-map.mdc"]
    L2Process --> L2Review["🔍 审查构建<br>计划"]
    L2Review --> L2Examine["👁️ 检查相关<br>代码区域"]
    L2Examine --> L2Implement["⚒️ 按顺序实现<br>变更"]
    L2Implement --> L2Test["✅ 测试<br>变更"]
    L2Test --> L2Update["📝 更新<br>tasks.md"]
    
    %% 级别 3-4 实现
    CheckLevel -->|"级别 3-4<br>功能/系统"| L34Process["🏗️ 级别 3-4 流程<br>.cursor/rules/isolation_rules/visual-maps/implement-mode-map.mdc"]
    L34Process --> L34Review["🔍 审查计划 &<br>创意决策"]
    L34Review --> L34Phase{"📋 选择<br>构建<br>阶段"}
    
    %% 实现阶段
    L34Phase --> L34Phase1["⚒️ 阶段 1<br>构建"]
    L34Phase1 --> L34Test1["✅ 测试<br>阶段 1"]
    L34Test1 --> L34Document1["📝 记录<br>阶段 1"]
    L34Document1 --> L34Next1{"📋 下一个<br>阶段？"}
    L34Next1 -->|"是"| L34Phase
    
    L34Next1 -->|"否"| L34Integration["🔄 集成<br>测试"]
    L34Integration --> L34Document["📝 记录<br>集成点"]
    L34Document --> L34Update["📝 更新<br>tasks.md"]
    
    %% 命令执行
    L1Fix & L2Implement & L34Phase1 --> CommandExec["⚙️ 命令执行<br>.cursor/rules/isolation_rules/Core/command-execution.mdc"]
    CommandExec --> DocCommands["📝 记录命令<br>& 结果"]
    
    %% 实现文档
    DocCommands -.-> DocTemplate["📋 构建文档:<br>- 代码变更<br>- 执行的命令<br>- 结果/观察<br>- 状态"]
    
    %% 完成与转换
    L1Update & L2Update & L34Update --> VerifyComplete["✅ 验证构建<br>完成"]
    VerifyComplete --> UpdateTasks["📝 最终更新<br>tasks.md"]
    UpdateTasks --> Transition["⏭️ 下一模式:<br>REFLECT 模式"]
    
    %% 验证选项
    Start -.-> Validation["🔍 验证选项:<br>- 审查构建计划<br>- 显示代码构建<br>- 记录命令执行<br>- 测试构建<br>- 显示模式转换"]
    
    %% 样式
    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style ReadDocs fill:#80bfff,stroke:#4da6ff,color:black
    style CheckLevel fill:#d94dbb,stroke:#a3378a,color:white
    style L1Process fill:#4dbb5f,stroke:#36873f,color:white
    style L2Process fill:#ffa64d,stroke:#cc7a30,color:white
    style L34Process fill:#ff5555,stroke:#cc0000,color:white
    style CommandExec fill:#d971ff,stroke:#a33bc2,color:white
    style VerifyComplete fill:#4dbbbb,stroke:#368787,color:white
    style Transition fill:#5fd94d,stroke:#3da336,color:white
```

## 构建步骤

### 步骤 1: 读取命令执行规则
```
read_file({
  target_file: ".cursor/rules/isolation_rules/Core/command-execution.mdc",
  should_read_entire_file: true
})
```

### 步骤 2: 读取任务和实现计划
```
read_file({
  target_file: "tasks.md",
  should_read_entire_file: true
})

read_file({
  target_file: "implementation-plan.md",
  should_read_entire_file: true
})
```

### 步骤 3: 加载实现模式图
```
read_file({
  target_file: ".cursor/rules/isolation_rules/visual-maps/implement-mode-map.mdc",
  should_read_entire_file: true
})
```

### 步骤 4: 加载复杂度特定的实现参考
根据从 tasks.md 确定的复杂度级别，加载：

#### 对于级别 1:
```
read_file({
  target_file: ".cursor/rules/isolation_rules/Level1/workflow-level1.mdc",
  should_read_entire_file: true
})
```

#### 对于级别 2:
```
read_file({
  target_file: ".cursor/rules/isolation_rules/Level2/workflow-level2.mdc",
  should_read_entire_file: true
})
```

#### 对于级别 3-4:
```
read_file({
  target_file: ".cursor/rules/isolation_rules/Phases/Implementation/implementation-phase-reference.mdc",
  should_read_entire_file: true
})

read_file({
  target_file: ".cursor/rules/isolation_rules/Level4/phased-implementation.mdc",
  should_read_entire_file: true
})
```

## 构建方法

您的任务是构建实现计划中定义的变更，如果适用，遵循创意阶段期间做出的决策。系统地执行变更，记录结果，并验证所有需求都得到满足。

### 级别 1: 快速错误修复构建

对于级别 1 任务，专注于实现特定问题的针对性修复。理解错误，检查相关代码，实现精确修复，并验证问题已解决。

```mermaid
graph TD
    L1["🔧 级别 1 构建"] --> Review["仔细审查问题"]
    Review --> Locate["定位导致问题的具体代码"]
    Locate --> Fix["实现针对性修复"]
    Fix --> Test["彻底测试以验证解决"]
    Test --> Doc["记录解决方案"]
    
    style L1 fill:#4dbb5f,stroke:#36873f,color:white
    style Review fill:#d6f5dd,stroke:#a3e0ae,color:black
    style Locate fill:#d6f5dd,stroke:#a3e0ae,color:black
    style Fix fill:#d6f5dd,stroke:#a3e0ae,color:black
    style Test fill:#d6f5dd,stroke:#a3e0ae,color:black
    style Doc fill:#d6f5dd,stroke:#a3e0ae,color:black
```

### 级别 2: 增强构建

对于级别 2 任务，根据计划阶段创建的计划实现变更。确保每个步骤在进入下一步之前都已完成和测试，在整个过程中保持清晰和专注。

```mermaid
graph TD
    L2["🔨 级别 2 构建"] --> Plan["遵循构建计划"]
    Plan --> Components["构建每个组件"]
    Components --> Test["测试每个组件"]
    Test --> Integration["验证集成"]
    Integration --> Doc["记录构建详情"]
    
    style L2 fill:#ffa64d,stroke:#cc7a30,color:white
    style Plan fill:#ffe6cc,stroke:#ffa64d,color:black
    style Components fill:#ffe6cc,stroke:#ffa64d,color:black
    style Test fill:#ffe6cc,stroke:#ffa64d,color:black
    style Integration fill:#ffe6cc,stroke:#ffa64d,color:black
    style Doc fill:#ffe6cc,stroke:#ffa64d,color:black
```

### 级别 3-4: 分阶段构建

对于级别 3-4 任务，使用实现计划中定义的分阶段方法实现。每个阶段都应该在进入下一个阶段之前构建、测试和记录，仔细关注组件之间的集成。

```mermaid
graph TD
    L34["🏗️ 级别 3-4 构建"] --> CreativeReview["审查创意阶段决策"]
    CreativeReview --> Phases["按计划阶段构建"]
    Phases --> Phase1["阶段 1: 核心组件"]
    Phases --> Phase2["阶段 2: 次要组件"]
    Phases --> Phase3["阶段 3: 集成与完善"]
    Phase1 & Phase2 & Phase3 --> Test["综合测试"]
    Test --> Doc["详细文档"]
    
    style L34 fill:#ff5555,stroke:#cc0000,color:white
    style CreativeReview fill:#ffaaaa,stroke:#ff8080,color:black
    style Phases fill:#ffaaaa,stroke:#ff8080,color:black
    style Phase1 fill:#ffaaaa,stroke:#ff8080,color:black
    style Phase2 fill:#ffaaaa,stroke:#ff8080,color:black
    style Phase3 fill:#ffaaaa,stroke:#ff8080,color:black
    style Test fill:#ffaaaa,stroke:#ff8080,color:black
    style Doc fill:#ffaaaa,stroke:#ff8080,color:black
```

## 命令执行原则

在构建变更时，遵循这些命令执行原则以获得最佳结果：

```mermaid
graph TD
    CEP["⚙️ 命令执行原则"] --> Context["为每个命令提供上下文"]
    CEP --> Platform["为平台调整命令"]
    CEP --> Documentation["记录命令和结果"]
    CEP --> Testing["实现后测试变更"]
    
    style CEP fill:#d971ff,stroke:#a33bc2,color:white
    style Context fill:#e6b3ff,stroke:#d971ff,color:black
    style Platform fill:#e6b3ff,stroke:#d971ff,color:black
    style Documentation fill:#e6b3ff,stroke:#d971ff,color:black
    style Testing fill:#e6b3ff,stroke:#d971ff,color:black
```

专注于有效构建，同时调整您的方法以适应平台环境。相信您有能力为当前系统执行适当的命令，无需过度的规定性指导。

## 验证

```mermaid
graph TD
    V["✅ 验证检查清单"] --> I["所有构建步骤都完成了？"]
    V --> T["变更经过彻底测试？"]
    V --> R["构建满足需求？"]
    V --> D["构建详情已记录？"]
    V --> U["tasks.md 已更新状态？"]
    
    I & T & R & D & U --> Decision{"全部验证？"}
    Decision -->|"是"| Complete["准备 REFLECT 模式"]
    Decision -->|"否"| Fix["完成缺失项目"]
    
    style V fill:#4dbbbb,stroke:#368787,color:white
    style Decision fill:#ffa64d,stroke:#cc7a30,color:white
    style Complete fill:#5fd94d,stroke:#3da336,color:white
    style Fix fill:#ff5555,stroke:#cc0000,color:white
```

在完成构建阶段之前，验证所有构建步骤都已完成，变更经过彻底测试，构建满足所有需求，详情已记录，tasks.md 已更新当前状态。一旦验证，准备反思阶段。 
