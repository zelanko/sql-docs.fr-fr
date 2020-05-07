---
title: Notebooks avec KQL (Kusto Query Language) magic dans Azure Data Studio
description: Ce tutoriel vous montre comment créer et exécuter Kqlmagic dans Azure Data Studio.
author: markingmyname
ms.author: maghan
ms.reviewer: jukoesma
ms.topic: conceptual
ms.prod: sql
ms.technology: azure-data-studio
ms.custom: ''
ms.date: 04/27/2020
ms.openlocfilehash: a3c4af3166d7c227af1846114321228af9ce7753
ms.sourcegitcommit: 69f93dd1afc0df76c3b4d9203adae0ad7dbd7bb2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82598725"
---
# <a name="kqlmagic-extension-in-azure-data-studio"></a>Extension Kqlmagic dans Azure Data Studio

**Kqlmagic** est une commande qui étend les fonctionnalités du noyau Python dans les **[notebooks Azure Data Studio](notebooks-guidance.md)** . Vous pouvez combiner Python et le **[langage de requête Kusto (KQL)](https://docs.microsoft.com/azure/data-explorer/kusto/query)** pour interroger et visualiser des données à l’aide de la bibliothèque Plot.ly enrichie intégrée avec les commandes `render`. Kqlmagic vous permet de bénéficier des avantages des notebooks, de l’analyse des données et des fonctionnalités Python riches dans un seul et même endroit. **[Azure Data Explorer](https://docs.microsoft.com/azure/data-explorer/data-explorer-overview)** , **[Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)** et les **[journaux Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-logs)** comptent parmi les sources de données prises en charge avec Kqlmagic.

Cet article explique comment créer et exécuter un notebook dans Azure Data Studio à l’aide de l’extension Kqlmagic pour un cluster Azure Data Explorer, un journal Application Insights et des journaux Azure Monitor.

## <a name="prerequisites"></a>Prérequis

- [Azure Data Studio](download-azure-data-studio.md)
- [Python](https://www.python.org/downloads/)

## <a name="install-and-set-up-kqlmagic-in-a-notebook"></a>Installer et configurer Kqlmagic dans un notebook

Les étapes de cette section s’exécutent toutes dans un notebook Azure Data Studio.

1. Créez un notebook et choisissez **Python 3** comme *Noyau*.

   ![Nouveau notebook](media/notebooks-kql-magic/install-new-notebook.png)

2. Quand vous y êtes invité, sélectionnez **Oui** pour mettre à niveau les packages Python.

   ![Oui](media/notebooks-kql-magic/install-python-yes.png)

3. Installer Kqlmagic :

   ```python
   !pip install Kqlmagic --no-cache-dir --upgrade
   ```

   Vérifiez qu’il est installé :

   ```python
   !pip list
   ```

   ![List](media/notebooks-kql-magic/install-list.png)

4. Charger Kqlmagic :

   ```python
   %reload_ext Kqlmagic
   ```

   > [!Note]
   > Si cette étape échoue, fermez le fichier et rouvrez-le.

   ![Charger l’extension Kqlmagic](media/notebooks-kql-magic/install-load-kql-magic-ext.png)

5. Vous pouvez tester si Kqlmagic est correctement chargé en parcourant la documentation d’aide ou en vérifiant la version.

   ```python
   %kql --help "help"
   ```

   > [!Note]
   > Si `Samples@help` demande un mot de passe, vous pouvez laisser ce champ vide et appuyer sur **Entrée**.

   ![Aide](media/notebooks-kql-magic/install-help.png)

   Pour voir quelle version de Kqlmagic est installée, exécutez la commande ci-dessous.

   ```python
   %kql --version
   ```

## <a name="kqlmagic-with-an-azure-data-explorer-cluster"></a>Kqlmagic avec un cluster Azure Data Explorer

Cette section explique comment exécuter l’analyse des données à l’aide de Kqlmagic avec un cluster Azure Data Explorer.

### <a name="load-and-authenticate-kqlmagic-for-azure-data-explorer"></a><a name="ade-load-auth"></a> Charger et authentifier Kqlmagic pour Azure Data Explorer

   > [!Note]
   > Chaque fois que vous créez un notebook dans Azure Data Studio, vous devez charger l’extension Kqlmagic.

1. Vérifiez que **Python 3** est sélectionné comme *Noyau*.

   ![Nouveau notebook](media/notebooks-kql-magic/change-kernel.png)

2. Charger Kqlmagic :

   ```python
   %reload_ext Kqlmagic
   ```

   ![Charger l’extension Kqlmagic](media/notebooks-kql-magic/install-load-kql-magic-ext.png)

3. Connectez-vous au cluster et authentifiez-vous :

   ```python
   %kql azureDataExplorer://code;cluster='help';database='Samples'
   ```

   Utilisez la connexion de l’appareil pour vous authentifier. Copiez le code à partir de la sortie et sélectionnez **authentifier** pour ouvrir un navigateur dans lequel vous devez coller le code. Une fois l’authentification terminée, vous pouvez revenir à Azure Data Studio pour continuer avec le reste du script.

   ![Authentification Azure Data Explorer](media/notebooks-kql-magic/ade-auth.png)

### <a name="query-and-visualize-for-azure-data-explorer"></a>Interroger et visualiser pour Azure Data Explorer

Interrogez les données à l’aide de l’[opérateur de rendu](https://docs.microsoft.com/azure/data-explorer/kusto/query/renderoperator) et visualisez les données à l’aide de la bibliothèque ploy.ly. Cette requête et cette visualisation fournit une expérience intégrée qui utilise KQL natif.

1. Analysez les 10 premiers événements Storm par état et par fréquence :

   ```python
   %kql StormEvents | summarize count() by State | sort by count_ | limit 10
   ```

   Si vous avez déjà utilisé le langage KQL (Kusto Query Language), vous pouvez taper la requête après `%kql`.

   ![Analyser les événements Storm](media/notebooks-kql-magic/ade-analyze-storm-events.png)

2. Visualisez un graphique chronologique :

   ```python
   %kql StormEvents \
   | summarize event_count=count() by bin(StartTime, 1d) \
   | render timechart title= 'Daily Storm Events'
   ```

   ![visualiser un graphique temporel](media/notebooks-kql-magic/ade-visualize-timechart.png)

3. Exemple de requête multiligne utilisant `%%kql`.

   ```python
   %%kql
   StormEvents
   | summarize count() by State
   | sort by count_
   | limit 10
   | render columnchart title='Top 10 States by Storm Event count'
   ```

   ![Exemple de requête multiligne](media/notebooks-kql-magic/ade-multiline-query-sample.png)

## <a name="kqlmagic-with-application-insights"></a>Kqlmagic avec Application Insights

### <a name="load-and-authenticate-kqlmagic-for-application-insights"></a><a name="appin-load-auth"></a> Charger et authentifier Kqlmagic pour Application Insights

1. Vérifiez que **Python 3** est sélectionné comme *Noyau*.

   ![Nouveau notebook](media/notebooks-kql-magic/change-kernel.png)

2. Charger Kqlmagic :

   ```python
   %reload_ext Kqlmagic
   ```

   ![Charger l’extension Kqlmagic](media/notebooks-kql-magic/install-load-kql-magic-ext.png)

   > [!Note]
   > Chaque fois que vous créez un notebook dans Azure Data Studio, vous devez charger l’extension Kqlmagic.

3. Procédez à la connexion et à l’authentification.

   ```python
   %kql appinsights://appid='DEMO_APP';appkey='DEMO_KEY'
   ```

### <a name="query-and-visualize-for-application-insights"></a>Interroger et visualiser pour Application Insights

Interrogez les données à l’aide de l’[opérateur de rendu](https://docs.microsoft.com/azure/data-explorer/kusto/query/renderoperator) et visualisez les données à l’aide de la bibliothèque ploy.ly. Cette requête et cette visualisation fournit une expérience intégrée qui utilise KQL natif.

1. Affichez les vues de page :

   ```python
   %%kql
   pageViews
   | limit 10
   ```

   ![Affichages de pages](media/notebooks-kql-magic/appin-page-views.png)

   > [!Note]
   > Faites glisser la souris sur une zone du graphique pour zoomer sur une ou plusieurs dates spécifiques.

2. Affichez les vues de page dans un graphique chronologique :

   ```python
   %%kql
   pageViews
   | summarize event_count=count() by name, bin(timestamp, 1d)
   | render timechart title= 'Daily Page Views'
   ```

   ![Graphique chronologique](media/notebooks-kql-magic/appin-timechart.png)

## <a name="kqlmagic-with-azure-monitor-logs"></a>Kqlmagic avec les journaux Azure Monitor

### <a name="load-and-authenticate-kqlmagic-for-azure-monitor-logs"></a><a name="aml-load-auth"></a> Charger et authentifier Kqlmagic pour les journaux Azure Monitor

1. Vérifiez que **Python 3** est sélectionné comme *Noyau*.

   ![Nouveau notebook](media/notebooks-kql-magic/change-kernel.png)

2. Charger Kqlmagic :

   ```python
   %reload_ext Kqlmagic
   ```

   ![Charger l’extension Kqlmagic](media/notebooks-kql-magic/install-load-kql-magic-ext.png)

   > [!Note]
   > Chaque fois que vous créez un notebook dans Azure Data Studio, vous devez charger l’extension Kqlmagic.

3. Procédez à la connexion et à l’authentification :

   ```python
   %kql loganalytics://workspace='DEMO_WORKSPACE';appkey='DEMO_KEY';alias='myworkspace'
   ```

   ![Authentification Log Analytics](media/notebooks-kql-magic/aml-auth.png)

### <a name="query-and-visualize-for-azure-monitor-logs"></a>Interroger et visualiser pour les journaux Azure Monitor

Interrogez les données à l’aide de l’[opérateur de rendu](https://docs.microsoft.com/azure/data-explorer/kusto/query/renderoperator) et visualisez les données à l’aide de la bibliothèque ploy.ly. Cette requête et cette visualisation fournit une expérience intégrée qui utilise KQL natif.

1. Affichez un graphique chronologique :

   ```python
   %%kql
   KubeNodeInventory
   | summarize event_count=count() by Status, bin(TimeGenerated, 1d)
   | render timechart title= 'Daily Kubernetes Nodes'
   ```

   ![Graphique temporel des nœuds Kubernetes quotidiens avec Log Analytics](media/notebooks-kql-magic/aml-timechart-daily-kubernetes-nodes.png)

## <a name="next-steps"></a>Étapes suivantes

Découvrez-en plus sur les notebooks et Kqlmagic :

- [Utiliser un notebook Jupyter et l’extension Kqlmagic pour analyser des données dans Azure Data Explorer](https://docs.microsoft.com/azure/data-explorer/Kqlmagic)
- [Extension (Magic) à Jupyter Notebook et JupyterLab offrant une expérience de notebook avec des données Kusto, Application Insights et Log Analytics](https://github.com/Microsoft/jupyter-Kqlmagic)
- [Kqlmagic](https://pypi.org/project/Kqlmagic/)
- [KustoMagicSamples](https://notebooks.azure.com/RknDzgn/projects/KustoMagicSamples/html/Getting%20Started%20with%20Kqlmagic%20on%20Azure%20Data%20Explorer-Copy.ipynb)
- [Guide pratique pour utiliser des notebooks](notebooks-guidance.md)
- [Comment gérer des notebooks dans Azure Data Studio](notebooks-manage-sql-server.md)
