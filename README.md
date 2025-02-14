# 🚀 Apache Superset com Docker

Este guia fornece instruções passo a passo para configurar e executar o Apache Superset usando Docker.

## 📋 Pré-requisitos

- Windows 10/11
- Docker Desktop instalado e em execução

## 🔧 Instalação e Configuração

### 1. Instalação do Docker Desktop

Primeiro, instale o Docker Desktop seguindo as instruções oficiais:
- [Download e Instalação do Docker Desktop para Windows](https://docs.docker.com/desktop/setup/install/windows-install/)

### 2. Configuração do Apache Superset

Siga os passos abaixo para configurar o Apache Superset:

#### 2.1 Download da Imagem
```bash
docker pull apache/superset
```

#### 2.2 Criação do Container
```bash
docker run -d -p 8080:8088 -e "SUPERSET_SECRET_KEY=your_secret_key_here" --name superset apache/superset
```

#### 2.3 Criação do Usuário Admin
```bash
docker exec -it superset superset fab create-admin --username admin --firstname Superset --lastname Admin --email admin@superset.com --password admin
```

#### 2.4 Atualização do Banco de Dados
```bash
docker exec -it superset superset db upgrade
```

#### 2.5 Carregamento de Exemplos (Opcional)
```bash
docker exec -it superset superset load_examples
```

#### 2.6 Inicialização do Superset
```bash
docker exec -it superset superset init
```

## 🌐 Acesso à Interface

Após a conclusão de todos os passos:
1. Abra seu navegador
2. Acesse: `http://localhost:8080`
   - Se não funcionar, tente: `http://localhost:8088` (porta original do Superset)
3. Faça login com as credenciais:
   - Usuário: `admin`
   - Senha: `admin`

## ⚠️ Observações Importantes

- Mantenha o Docker Desktop em execução para usar o Superset
- Altere a senha padrão do admin após o primeiro acesso
- O carregamento de exemplos é opcional, mas recomendado para usuários iniciantes
- A porta padrão configurada é 8080, certifique-se de que ela esteja disponível

## 🛟 Solução de Problemas

Se encontrar problemas:
1. Verifique se o Docker Desktop está em execução
2. Confirme se a porta 8080 não está sendo usada por outro serviço
3. Verifique os logs do container usando:
   ```bash
   docker logs superset
   ```

## 🔄 Comandos Úteis

- Parar o container: `docker stop superset`
- Iniciar o container: `docker start superset`
- Reiniciar o container: `docker restart superset`
- Remover o container: `docker rm superset`

## 📚 Links Úteis

- [Documentação Oficial do Apache Superset](https://superset.apache.org/docs/intro)
- [Documentação do Docker](https://docs.docker.com/)
- [GitHub do Apache Superset](https://github.com/apache/superset)

---
⭐ Se este guia foi útil, considere dar uma estrela no repositório!

## 📊 Exemplos de Dashboards

Aqui estão alguns exemplos do que você pode criar com o Apache Superset:

### Dashboard de Vendas
![Dashboard de Vendas](https://raw.githubusercontent.com/apache/superset/master/superset-frontend/src/assets/images/explore.jpg)
*Dashboard mostrando análise de vendas com diferentes visualizações como gráficos de barras, linhas e indicadores de desempenho.*

### Análise Geográfica
![Análise Geográfica](https://raw.githubusercontent.com/apache/superset/master/superset-frontend/src/assets/images/dashboard.jpg)
*Exemplo de dashboard com mapas e análises geográficas, permitindo visualizar dados distribuídos por região.*

### Principais Recursos de Visualização:
- Gráficos de linha e área para análise de tendências
- Gráficos de barra e colunas para comparações
- Mapas de calor e dispersão
- Gráficos de pizza e rosca
- Tabelas dinâmicas
- Mapas geográficos
- Indicadores e métricas em tempo real
- Filtros interativos
- Dashboards responsivos

### Exemplos de Uso:
1. **Monitoramento de Vendas**
   - Acompanhamento de receita diária/mensal
   - Análise de produtos mais vendidos
   - Performance por região/vendedor

2. **Análise Financeira**
   - Acompanhamento de despesas
   - Análise de lucratividade
   - Projeções financeiras

3. **Marketing Digital**
   - Métricas de campanhas
   - Análise de conversão
   - Comportamento do usuário

4. **Operações**
   - Monitoramento de estoque
   - Eficiência operacional
   - Controle de qualidade

Estes são apenas alguns exemplos do potencial do Apache Superset. A ferramenta é altamente customizável e pode ser adaptada para diversos casos de uso e necessidades específicas.
