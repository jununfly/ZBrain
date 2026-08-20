# Merge from gbrain

本文件记录 ZBrain 与上游 `garrytan/gbrain` 的来源关系，以及尚未解决的同步策略问题。

## 来源（Provenance）

- **本仓库** `jununfly/ZBrain` 是 `garrytan/gbrain` 的派生（fork）。
  - 本地 git remote 约定：
    - `origin` → `git@github.com:jununfly/ZBrain.git`（你自己的仓库，推送目标）
    - `upstream` → `git@github.com:garrytan/gbrain.git`（上游，仅供 `fetch` / `merge from gbrain` 使用，不要直接推）
- **当前 `main` 分支固定在 gbrain 的上游 tag `v0.46.24.0`**（该 tag 同时带 `latest-stable` 别名）。
  - 选择该 tag 的原因：稳定、bug 较少，作为改写起点最省心。
  - `main` 当前 = gbrain 在 `v0.46.24.0` 处的完整历史快照，尚未做任何 ZBrain 改写。
- 本仓库在此 tag 基础上仅追加了 `docs/depends/` 下的说明文件（即本文件），其余代码与上游一致。

## 上游同步策略（待定）

> **遗留 TODO**：未来对 ZBrain 改写比较多之后，应该怎么 `merge from gbrain`？
>
> 需要回答的核心问题——**merge item 的映射关系是什么**：
> 上游 `garrytan/gbrain` 的某一次改动（commit / PR / 文件级 diff），
> 对应到 ZBrain 的哪一处？尤其是：
> - 上游是 TypeScript / Bun；ZBrain 若是 Rust 改写，模块粒度、目录结构、命名都可能不同，
>   无法简单 `git merge upstream/master`，需要一个**映射表 / 改写规则**来描述
>   "上游的 X 对应 ZBrain 的 Y"。
> - 哪些上游改动值得同步（bug fix / 协议变更），哪些不应同步（与 ZBrain 设计背离的部分）。
>
> 目前尚未建立该映射表。建议在 ZBrain 改写铺开、模块边界稳定后再补，
> 届时可结合 `docs/` 下已有的 design / architecture 文档一起定义映射关系。

## 参考

- 上游仓库：https://github.com/garrytan/gbrain
- 锁定 tag：`v0.46.24.0`（别名 `latest-stable`）
- 同步命令参考（未来）：`git fetch upstream` → 视映射关系 cherry-pick / merge 对应 item
