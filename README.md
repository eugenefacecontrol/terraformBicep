### Шаг 1. Bicep

Ниже приведены примерные команды для создания Resource Group и развертывания Bicep-шаблона, а также проверка ресурсов в группе. В примере используется Powershell.

```bash
# 1. Создание Resource Group
az group create `
  --name myResourceGroupAG `
  --location eastus

# 2. Развертывание Bicep-файла
az deployment group create `
  --resource-group myResourceGroupAG `
  --template-file main.bicep `
  --parameters adminUsername=<admin-username>

# 3. Список ресурсов в группе
az resource list `
  --resource-group myResourceGroupAG
```

Дополнительные сведения:
[Deploy the Bicep file](https://learn.microsoft.com/en-us/azure/application-gateway/quick-create-bicep?tabs=CLI#deploy-the-bicep-file)

---

### Шаг 2. Terraform

Ниже — примерный цикл развёртывания для Terraform (инициализация, планирование, применение) и команда для вывода адреса фронтенда. Предполагается, что вы уже создали `main.tf` или другой `.tf` файл с конфигурацией.

```bash
# 1. Инициализация Terraform (обновит провайдеры до последних версий)
terraform init -upgrade

# 2. Создание плана
terraform plan -out main.tfplan

# 3. Применение плана
terraform apply main.tfplan

# 4. Отображение IP-адреса (пример, если в output определён gateway_frontend_ip)
echo $(terraform output -raw gateway_frontend_ip)
```

Подробнее:
[Quick Create with Terraform](https://learn.microsoft.com/en-us/azure/application-gateway/quick-create-terraform#create-a-terraform-execution-plan)