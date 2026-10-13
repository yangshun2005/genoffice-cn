# GenOffice 企业版（`ee/`）

本目录预留给未来的企业模块（例如私有化部署和离线许可证验证）。目前除本说明和许可证外，目录有意保持为空。

## 许可证边界

`ee/` 下的所有内容均受 [GenOffice 企业版许可证](LICENSE) 约束，而非覆盖仓库其余部分的 Apache-2.0 许可证。将所有企业代码集中在这一个顶层目录下，可使许可证边界易于审计，并让开源核心永久保持纯 Apache-2.0。

## 贡献

`ee/` 不接受外部贡献。维护者团队之外的 Pull Request 不得修改本目录中的文件（通过 CODEOWNERS 强制执行）。参见 [CONTRIBUTING.md](../CONTRIBUTING.md)。