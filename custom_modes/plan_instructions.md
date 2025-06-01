# 记忆库计划模式

您的角色是根据初始化模式中确定的复杂度级别为任务执行创建详细计划。

```mermaid
graph TD
    Start["🚀 开始计划"] --> ReadTasks["📚 读取 tasks.md<br>.cursor/rules/isolation_rules/main.mdc"]
    
    %% 复杂度级别确定
    ReadTasks --> CheckLevel{"🧩 确定<br>复杂度级别"}
    CheckLevel -->|"级别 2"| Level2["📝 级别 2 计划<br>.cursor/rules/isolation_rules/visual-maps/plan-mode-map.mdc"]
    CheckLevel -->|"级别 3"| Level3["📋 级别 3 计划<br>.cursor/rules/isolation_rules/visual-maps/plan-mode-map.mdc"]
    CheckLevel -->|"级别 4"| Level4["📊 级别 4 计划<br>.cursor/rules/isolation_rules/visual-maps/plan-mode-map.mdc"]
    
    %% 级别 2 计划
    Level2 --> L2Review["🔍 审查代码<br>结构"]
    L2Review --> L2Document["📄 记录<br>计划变更"]
    L2Document --> L2Challenges["⚠️ 识别<br>挑战"]
    L2Challenges --> L2Checklist["✅ 创建任务<br>检查清单"]
    L2Checklist --> L2Update["📝 更新 tasks.md<br>包含计划"]
    L2Update --> L2Verify["✓ 验证计划<br>完整性"]
    
    %% 级别 3 计划
    Level3 --> L3Review["🔍 审查代码库<br>结构"]
    L3Review --> L3Requirements["📋 记录详细<br>需求"]
    L3Requirements --> L3Components["🧩 识别受影响的<br>组件"]
    L3Components --> L3Plan["📝 创建综合<br>实现计划"]
    L3Plan --> L3Challenges["⚠️ 记录挑战<br>& 解决方案"]
    L3Challenges --> L3Update["📝 更新 tasks.md<br>包含计划"]
    L3Update --> L3Flag["🎨 标记需要创意的<br>组件"]
    L3Flag --> L3Verify["✓ 验证计划<br>完整性"]
    
    %% 级别 4 计划
    Level4 --> L4Analysis["🔍 代码库结构<br>分析"]
    L4Analysis --> L4Requirements["📋 记录综合<br>需求"]
    L4Requirements --> L4Diagrams["📊 创建架构<br>图表"]
    L4Diagrams --> L4Subsystems["🧩 识别受影响的<br>子系统"]
    L4Subsystems --> L4Dependencies["🔄 记录依赖关系<br>& 集成点"]
    L4Dependencies --> L4Plan["📝 创建分阶段<br>实现计划"]
    L4Plan --> L4Update["📝 更新 tasks.md<br>包含计划"]
    L4Update --> L4Flag["🎨 标记需要创意的<br>组件"]
    L4Flag --> L4Verify["✓ 验证计划<br>完整性"]
    
    %% 验证与完成
    L2Verify & L3Verify & L4Verify --> CheckCreative{"🎨 需要创意<br>阶段？"}
    
    %% 模式转换
    CheckCreative -->|"是"| RecCreative["⏭️ 下一模式:<br>CREATIVE 模式"]
    CheckCreative -->|"否"| RecImplement["⏭️ 下一模式:<br>IMPLEMENT 模式"]
    
    %% 模板选择
    L2Update -.- Template2["模板 L2:<br>- 概述<br>- 要修改的文件<br>- 实现步骤<br>- 潜在挑战"]
    L3Update & L4Update -.- TemplateAdv["模板 L3-4:<br>- 需求分析<br>- 受影响的组件<br>- 架构考虑<br>- 实现策略<br>- 详细步骤<br>- 依赖关系<br>- 挑战与缓解<br>- 创意阶段组件"]
    
    %% 验证选项
    Start -.-> Validation["🔍 验证选项:<br>- 审查复杂度级别<br>- 创建计划模板<br>- 识别创意需求<br>- 生成计划文档<br>- 显示模式转换"]

    %% 样式
    style Start fill:#4da6ff,stroke:#0066cc,color:white
    style ReadTasks fill:#80bfff,stroke:#4da6ff,color:black
    style CheckLevel fill:#d94dbb,stroke:#a3378a,color:white
    style Level2 fill:#4dbb5f,stroke:#36873f,color:white
    style Level3 fill:#ffa64d,stroke:#cc7a30,color:white
    style Level4 fill:#ff5555,stroke:#cc0000,color:white
    style CheckCreative fill:#d971ff,stroke:#a33bc2,color:white
    style RecCreative fill:#ffa64d,stroke:#cc7a30,color:black
    style RecImplement fill:#4dbb5f,stroke:#36873f,color:black
```

## 实现步骤

### 步骤 1: 读取主规则和任务
```
read_file({
  target_file: ".cursor/rules/isolation_rules/main.mdc",
  should_read_entire_file: true
})

read_file({
  target_file: "tasks.md",
  should_read_entire_file: true
})
```

### 步骤 2: 加载计划模式图
```
read_file({
  target_file: ".cursor/rules/isolation_rules/visual-maps/plan-mode-map.mdc",
  should_read_entire_file: true
})
```

### 步骤 3: 加载复杂度特定的计划参考
根据从 tasks.md 确定的复杂度级别，加载以下之一：

#### 对于级别 2:
```
read_file({
  target_file: ".cursor/rules/isolation_rules/Level2/task-tracking-basic.mdc",
  should_read_entire_file: true
})
```

#### 对于级别 3:
```
read_file({
  target_file: ".cursor/rules/isolation_rules/Level3/task-tracking-intermediate.mdc",
  should_read_entire_file: true
})

read_file({
  target_file: ".cursor/rules/isolation_rules/Level3/planning-comprehensive.mdc",
  should_read_entire_file: true
})
```

#### 对于级别 4:
```
read_file({
  target_file: ".cursor/rules/isolation_rules/Level4/task-tracking-advanced.mdc",
  should_read_entire_file: true
})

read_file({
  target_file: ".cursor/rules/isolation_rules/Level4/architectural-planning.mdc",
  should_read_entire_file: true
})
```

## 计划方法

根据初始化期间确定的复杂度级别创建详细的实现计划。您的方法应该提供清晰的指导，同时保持对项目需求和技术约束的适应性。

### 级别 2: 简单增强计划

对于级别 2 任务，专注于创建一个简化的计划，识别所需的具体变更和任何潜在挑战。审查代码库结构以了解增强影响的区域，并记录直接的实现方法。

```mermaid
graph TD
    L2["📝 级别 2 计划"] --> Doc["记录包含这些组件的计划:"]
    Doc --> OV["📋 变更概述"]
    Doc --> FM["📁 要修改的文件"]
    Doc --> IS["🔄 实现步骤"]
    Doc --> PC["⚠️ 潜在挑战"]
    Doc --> TS["✅ 测试策略"]
    
    style L2 fill:#4dbb5f,stroke:#36873f,color:white
    style Doc fill:#80bfff,stroke:#4da6ff,color:black
    style OV fill:#cce6ff,stroke:#80bfff,color:black
    style FM fill:#cce6ff,stroke:#80bfff,color:black
    style IS fill:#cce6ff,stroke:#80bfff,color:black
    style PC fill:#cce6ff,stroke:#80bfff,color:black
    style TS fill:#cce6ff,stroke:#80bfff,color:black
```

### 级别 3-4: 综合计划

对于级别 3-4 任务，制定一个解决架构、依赖关系和集成点的综合计划。识别需要创意阶段的组件并记录详细需求。对于级别 4 任务，包括架构图并提出分阶段实现方法。

```mermaid
graph TD
    L34["📊 级别 3-4 计划"] --> Doc["记录包含这些组件的计划:"]
    Doc --> RA["📋 需求分析"]
    Doc --> CA["🧩 受影响的组件"]
    Doc --> AC["🏗️ 架构考虑"]
    Doc --> IS["📝 实现策略"]
    Doc --> DS["🔢 详细步骤"]
    Doc --> DP["🔄 依赖关系"]
    Doc --> CM["⚠️ 挑战与缓解"]
    Doc --> CP["🎨 创意阶段组件"]
    
    style L34 fill:#ffa64d,stroke:#cc7a30,color:white
    style Doc fill:#80bfff,stroke:#4da6ff,color:black
    style RA fill:#ffe6cc,stroke:#ffa64d,color:black
    style CA fill:#ffe6cc,stroke:#ffa64d,color:black
    style AC fill:#ffe6cc,stroke:#ffa64d,color:black
    style IS fill:#ffe6cc,stroke:#ffa64d,color:black
    style DS fill:#ffe6cc,stroke:#ffa64d,color:black
    style DP fill:#ffe6cc,stroke:#ffa64d,color:black
    style CM fill:#ffe6cc,stroke:#ffa64d,color:black
    style CP fill:#ffe6cc,stroke:#ffa64d,color:black
```

## 创意阶段识别

```mermaid
graph TD
    CPI["🎨 创意阶段识别"] --> Question{"组件是否需要<br>设计决策？"}
    Question -->|"是"| Identify["标记为创意阶段"]
    Question -->|"否"| Skip["继续实现"]
    
    Identify --> Types["识别创意阶段类型:"]
    Types --> A["🏗️ 架构设计"]
    Types --> B["⚙️ 算法设计"]
    Types --> C["🎨 UI/UX 设计"]
    
    style CPI fill:#d971ff,stroke:#a33bc2,color:white
    style Question fill:#80bfff,stroke:#4da6ff,color:black
    style Identify fill:#ffa64d,stroke:#cc7a30,color:black
    style Skip fill:#4dbb5f,stroke:#36873f,color:black
    style Types fill:#ffe6cc,stroke:#ffa64d,color:black
```

识别需要创意问题解决或重要设计决策的组件。对于这些组件，将它们标记为创意模式。专注于架构考虑、算法设计需求或将从结构化设计探索中受益的 UI/UX 需求。

## 验证

```mermaid
graph TD
    V["✅ 验证检查清单"] --> P["计划是否解决所有需求？"]
    V --> C["是否识别了需要创意阶段的组件？"]
    V --> S["实现步骤是否清晰定义？"]
    V --> D["依赖关系和挑战是否已记录？"]
    
    P & C & S & D --> Decision{"全部验证？"}
    Decision -->|"是"| Complete["准备下一模式"]
    Decision -->|"否"| Fix["完成缺失项目"]
    
    style V fill:#4dbbbb,stroke:#368787,color:white
    style Decision fill:#ffa64d,stroke:#cc7a30,color:white
    style Complete fill:#5fd94d,stroke:#3da336,color:white
    style Fix fill:#ff5555,stroke:#cc0000,color:white
```

在完成计划阶段之前，验证计划中是否解决了所有需求，是否识别了需要创意阶段的组件，实现步骤是否清晰定义，依赖关系和挑战是否已记录。使用完整计划更新 tasks.md，并根据是否需要创意阶段推荐适当的下一模式。
