# 设置私有仓库统计

当前GitHub主页的统计**只包含公开仓库**,所以看不到你在Cepton写的C/C++代码。

要包含私有仓库的统计,需要以下步骤:

---

## 步骤1: 创建 Personal Access Token

1. **访问**: https://github.com/settings/tokens/new

2. **填写**:
   - **Note**: `METRICS_TOKEN`
   - **Expiration**: 选择 `No expiration` 或 `1 year`

3. **勾选权限** (Select scopes):
   ```
   ✅ repo (Full control of private repositories)
      ✅ repo:status
      ✅ repo_deployment
      ✅ public_repo
      ✅ repo:invite
      ✅ security_events
   ✅ read:org
   ✅ read:user
   ✅ read:project
   ```

4. **点击**: `Generate token` (绿色按钮)

5. **复制token**:
   - 格式: `ghp_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx`
   - ⚠️ 只显示一次,立即复制保存!

---

## 步骤2: 添加到 GitHub Secrets

1. **访问**: https://github.com/ProbeYuki/ProbeYuki/settings/secrets/actions

2. **点击**: `New repository secret` (右上角绿色按钮)

3. **填写**:
   - **Name**: `METRICS_TOKEN` (必须完全一致!)
   - **Secret**: 粘贴刚才复制的token

4. **点击**: `Add secret`

---

## 步骤3: 手动运行 Workflow

1. **访问**: https://github.com/ProbeYuki/ProbeYuki/actions

2. **点击**: `Update GitHub Stats with Private Repos` workflow

3. **点击**: `Run workflow` → `Run workflow`

4. **等待**: 大约1-2分钟

5. **刷新**: https://github.com/ProbeYuki

---

## 预期结果

设置完成后,你会看到:
- ✅ C/C++ 占比 ~21%
- ✅ Python 占比 ~18%
- ✅ 总提交数大幅增加(包含Cepton的提交)
- ✅ 更准确的语言使用统计

---

## 问题排查

如果统计还是不对:
1. 检查Token权限是否包含 `repo`
2. 检查Secret名称是否完全是 `METRICS_TOKEN`
3. 查看Actions运行日志: https://github.com/ProbeYuki/ProbeYuki/actions
4. 确认你在Cepton的仓库身份是 owner/collaborator/organization_member
