---
title: Didacticiel pour l’analytique en base de données à l’aide de R et SQL Server Machine Learning | Microsoft Docs
description: Didacticiel expliquant comment incorporer R dans SQL Server des procédures stockées et fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 07/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 8c7296c46bb6312d66c07c0bb63c9e97c37ec1db
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39082431"
---
# <a name="tutorial-learn-in-database-analytics-using-r-in-sql-server"></a>: Didacticiel analytique en base de données à l’aide de R dans SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Dans ce didacticiel pour les programmeurs SQL, vous acquérez une expérience pratique à l’aide du langage R pour générer et déployer une solution d’apprentissage en encapsulant le code R dans les procédures stockées.

Ce didacticiel utilise un dataset public bien connu, selon les allers-retours dans les taxis de New York city. Pour exécuter l’exemple de code plus rapidement, nous avons créé un échantillon représentatif de 1 % des données. Vous utiliserez ces données pour générer un modèle de classification binaire qui prédit si un voyage en particulier est susceptible d’obtienne un pourboire ou non, selon les colonnes telles que l’heure de la journée, distance et l’emplacement de la prise en charge.

> [!NOTE]
> 
> La même solution est disponible dans Python. SQL Server 2017 est requis. Consultez [en base de données analytique pour les développeurs Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>Vue d'ensemble

Le processus de création d’une solution de bout en bout généralement se compose d’obtention et le nettoyage des données, l’exploration de données et ingénierie des fonctionnalités, apprentissage du modèle et de paramétrage et enfin déploiement du modèle en production. Développement et le test du code réel est préférable d’effectuer à l’aide d’un environnement de développement dédié. Pour R, cela peut signifier que RStudio ou [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)].

Toutefois, une fois que la solution est créée, vous pouvez facilement la déployer sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] dans l’environnement familier de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

- [Leçon 1 : Télécharger les exemples de données et les scripts](../tutorials/sqldev-download-the-sample-data.md)

- [Leçon 2 : Configuration de l’environnement de didacticiel](../r/sqldev-import-data-to-sql-server-using-powershell.md)

- [Leçon 3 : Explorer et visualiser la forme de données et la distribution en appelant des fonctions R dans les procédures stockées](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Leçon 4 : Créer des fonctionnalités de données à l’aide de R dans les fonctions T-SQL](../tutorials/sqldev-create-data-features-using-t-sql.md)
  
- [Leçon 5 : Former et enregistrer un modèle R à l’aide des fonctions et procédures stockées](../r/sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Leçon 6 : Code de retour à la ligne R dans une procédure stockée pour l’Opérationnalisation](../tutorials/sqldev-operationalize-the-model.md). 
  Une fois que le modèle a été enregistré dans la base de données, appelez-le pour la prédiction dans [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide de procédures stockées.

## <a name="prerequisites"></a>Prérequis

Ce didacticiel suppose que vous êtes familiarisé avec les opérations de base de données telles que la création de tables et des bases de données, l’importation de données et l’écriture des requêtes SQL. Il ne suppose pas que vous R. Par conséquent, tout le code R est fourni. Un programmeur SQL expérimenté peut utiliser un script PowerShell fourni, exemples de données sur GitHub, et [!INCLUDE[tsql](../../includes/tsql-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour terminer cet exemple. 

Avant de commencer le didacticiel :

- Vérifiez que vous avez une instance configurée de [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) ou [SQL Server 2017 Machine Learning Services r activés](../install/sql-machine-learning-services-windows-install.md#verify-installation). En outre, [Confirmez que les bibliothèques R](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).
- La connexion que vous utilisez pour ce didacticiel doit avoir les autorisations nécessaires pour créer des bases de données et autres objets, pour charger des données, sélectionnez les données et exécuter des procédures stockées.

> [!NOTE]
> Nous vous recommandons d’effectuer **pas** utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour écrire ou tester le code R. Si le code que vous incorporez dans une procédure stockée a des problèmes, les informations retournées par la procédure stockée ne permettent généralement pas d’identifier la cause de l’erreur.
> 
> Pour le débogage, nous vous recommandons d’utiliser un outil tel que [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)], ou RStudio. Les scripts R fournis dans ce didacticiel ont déjà été développés et débogués à l’aide des outils R traditionnels.

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Leçon 1 : Télécharger les exemples de données](../tutorials/sqldev-download-the-sample-data.md)