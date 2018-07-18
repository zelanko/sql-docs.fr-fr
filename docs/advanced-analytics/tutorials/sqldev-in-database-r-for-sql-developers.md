---
title: Didacticiel d’analytique R incorporé pour les développeurs de SQL Server Machine Learning | Documents Microsoft
description: Le didacticiel expliquant comment incorporer R dans SQL Server procédures stockées et fonctions T-SQL
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/07/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 3d2b77d73bb1b8f5d4c507b884d0a09f4647012b
ms.sourcegitcommit: b52b5d972b1a180e575dccfc4abce49af1a6b230
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2018
ms.locfileid: "35250022"
---
# <a name="tutorial-embedded-r-in-stored-procedures-and-t-sql-functions"></a>Didacticiel : Incorporé R dans les procédures stockées et fonctions de T-SQL
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

L’objectif de ce didacticiel est de fournir des programmeurs SQL avec une expérience pratique de créer une solution dans SQL Server d’apprentissage. Dans ce didacticiel, vous allez apprendre à intégrer R dans une application ou d’une solution Décisionnelle en insérant le code R dans les procédures stockées.

> [!NOTE]
> 
> La même solution est disponible dans Python. SQL Server 2017 est requis. Consultez [dans-base de données analytique pour les développeurs Python](../tutorials/sqldev-in-database-python-for-sql-developers.md)

## <a name="overview"></a>Vue d'ensemble

Le processus de création d’une solution de bout en bout comprend généralement l’obtention et le nettoyage des données, l’exploration des données et l’ingénierie des caractéristiques, l’apprentissage et le réglage de modèles, et enfin le déploiement du modèle en production. Développement et test du code réel est préférable d’effectuer à l’aide d’un environnement de développement dédié. Pour R, cela peut signifier que RStudio ou [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)].

Toutefois, une fois que la solution est créée, vous pouvez facilement la déployer sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide de procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] dans l’environnement familier de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].

Dans ce didacticiel, nous supposons que vous avez reçu tout le code R requis pour la solution, puis de se concentrer sur la création et déploiement de la solution à l’aide de SQL Server.

- [Leçon 1 : Télécharger les exemples de données et les scripts](../tutorials/sqldev-download-the-sample-data.md)

- [Leçon 2 : Configurer l’environnement du didacticiel](../r/sqldev-import-data-to-sql-server-using-powershell.md)

- [Leçon 3 : Explorer et visualiser la forme de données et la distribution en appelant les fonctions R dans des procédures stockées](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [Leçon 4 : Créer des fonctionnalités de données à l’aide de R dans les fonctions T-SQL](../tutorials/sqldev-create-data-features-using-t-sql.md)
  
- [Leçon 5 : L’apprentissage et enregistrer un modèle R à l’aide des fonctions et procédures stockées](../r/sqldev-train-and-save-a-model-using-t-sql.md)
  
- [Leçon 6 : Code de retour à la ligne R dans une procédure stockée à l’Opérationnalisation](../tutorials/sqldev-operationalize-the-model.md). 
  Une fois que le modèle a été enregistré dans la base de données, appelez-le pour la prédiction dans [!INCLUDE[tsql](../../includes/tsql-md.md)] à l’aide de procédures stockées.

## <a name="scenario"></a>Scénario

Ce didacticiel utilise un dataset publique connu, basé sur les boucles dans taxi de New York city. Pour exécuter l’exemple de code plus rapide, nous avons créé un échantillonnage représentatif de 1 % des données. Ces données vous permet de générer un modèle de classification binaire qui prévoit si un voyage particulier est susceptible d’obtenir un Conseil ou non, en fonction des colonnes, telles que l’heure du jour, distance et l’emplacement d’extraction.

## <a name="requirements"></a>Spécifications

Ce didacticiel suppose que vous êtes familiarisé avec les opérations de base de données telles que la création de bases de données et de tables, l’importation de données et l’écriture de requêtes SQL. Il n’assume pas que vous savez R. Par conséquent, tout le code R est fourni. Un programmeur expérimenté de SQL peut utiliser un script PowerShell fourni, exemples de données sur GitHub, et [!INCLUDE[tsql](../../includes/tsql-md.md)] dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour compléter cet exemple. 

Avant de commencer le didacticiel :

- Vérifiez que vous avez une instance configurée de [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation) ou [SQL Server 2017 Machine Learning Services avec R activé](../install/sql-machine-learning-services-windows-install.md#verify-installation). En outre, [Confirmez que les bibliothèques R](../r/determine-which-packages-are-installed-on-sql-server.md#get-the-r-library-location).
- La connexion que vous utilisez pour ce didacticiel doit avoir les autorisations nécessaires pour créer des bases de données et autres objets, télécharger des données, sélectionnez les données et exécuter des procédures stockées.

> [!NOTE]
> Nous vous recommandons d’effectuer **pas** utiliser [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour écrire ou de tester le code R. Si le code que vous incorporez dans une procédure stockée a des problèmes, les informations retournées par la procédure stockée sont généralement insuffisant pour comprendre la cause de l’erreur.
> 
> Pour le débogage, nous vous recommandons d’utiliser un outil tel que [!INCLUDE[rtvs-short](../../includes/rtvs-short-md.md)], ou RStudio. Les scripts R fournis dans ce didacticiel ont déjà été développés et débogués à l’aide des outils R traditionnels.

## <a name="next-lesson"></a>Leçon suivante

[Leçon 1 : Télécharger les exemples de données](../tutorials/sqldev-download-the-sample-data.md)
