---
title: "Fonctions scaleR pour travailler avec des donn&#233;es SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "01/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "R"
ms.assetid: 5f3c9864-9c75-4688-947d-0940045b2671
caps.latest.revision: 9
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 7
---
# Fonctions scaleR pour travailler avec des donn&#233;es SQL Server
Cette rubrique fournit une vue d’ensemble des principales fonctions ScaleR pour une utilisation avec SQL Server, ainsi que des commentaires sur leur syntaxe.

Pour obtenir une liste complète des fonctions de DETARTREUR et comment les utiliser, consultez le [Microsoft R Server](https://msdn.microsoft.com/microsoft-r/index#) référence dans la bibliothèque MSDN. 

## Fonctions permettant de travailler avec des Sources de données SQL Server
Les fonctions suivantes permettent de définir un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] source de données. Un objet de source de données est un conteneur qui spécifie une chaîne de connexion avec le jeu de données que vous souhaitez, défini sous la forme d’une table, une vue ou une requête. Appels de procédures stockées ne sont pas pris en charge.  

Outre la définition d’une source de données, vous pouvez exécuter des instructions DDL à partir de R, si vous avez les autorisations nécessaires sur l’instance et de la base de données. 
+ [RxSqlServerData](https://msdn.microsoft.com/microsoft-r/scaler/RxSqlServerData) -définir une [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] objet source de données
+ [rxSqlServerDropTable](https://msdn.microsoft.com/microsoft-r/scaler/rxSqlServerDropTable) -Supprimer un [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] table
+ [rxSqlServerTableExists](https://msdn.microsoft.com/microsoft-r/scaler/rxSqlServerTableExists) -vérifier l’existence d’un objet ou une table de base de données
+ [rxExecuteSQLDDL](https://msdn.microsoft.com/microsoft-r/scaler/rxExecuteSQLDDL) - exécuter une commande pour définir, manipuler ou de contrôler les données SQL, mais pas retourner des données  

## Fonctions de définition ou de la gestion d’un contexte de calcul
Les fonctions suivantes permettent de définir un nouveau contexte de calcul, changer de contexte de calcul ou identifier le contexte de calcul en cours.
+ [RxComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/RxComputeContext) -créer un contexte de calcul. 
+ [rxInSqlServer](https://msdn.microsoft.com/microsoft-r/scaler/rxInSqlServer) -Générer un contexte de calcul de SQL Server qui vous permet de **ScaleR** fonctions s’exécutent dans les Services de R SQL Server.
+ [rxGetComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/rxGetComputeContext) -obtenir le contexte de calcul actuel. 
+ [rxSetComputeContext](https://msdn.microsoft.com/microsoft-r/scaler/rxSetComputeContext) -spécifier lequel calculer le contexte à utiliser. 

## Fonctions pour l’utilisation d’une Source de données
Après avoir créé un objet de source de données, vous pouvez l’ouvrir pour obtenir des données, ou écrire les nouvelles données. Selon la taille des données dans la source, vous pouvez également définir la taille de lot dans le cadre de la source de données et déplacer les données en segments. 
+ [rxIsOpen](https://msdn.microsoft.com/microsoft-r/scaler/rxIsOpen) -vérifie si une source de données est disponible
+ [rxOpen](https://msdn.microsoft.com/microsoft-r/scaler/rxOpen) -Ouvrir une source de données pour la lecture
+ [rxReadNext](https://msdn.microsoft.com/microsoft-r/scaler/rxReadNext) -lire des données à partir d’une source
+ [rxWriteNext](https://msdn.microsoft.com/microsoft-r/scaler/rxWriteNext) -écrire des données dans la cible
+ [rxClose](https://msdn.microsoft.com/microsoft-r/scaler/rxclose) -Fermer une source de données

Pour plus d’informations sur l’utilisation de ces fonctions ScaleR, qui peut fonctionner avec des sources de données autres que [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], consultez [ Microsoft R Server - mise en route](http://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started).

## Fonctions qui utilisent des fichiers de XDF
Les fonctions suivantes peuvent être utilisées pour créer un cache de données local dans le format XDF. Ce fichier peut être utile lorsque vous travaillez avec plus de données peuvent être transférées à partir de la base de données dans un lot, ou plus de données que vous pouvez tenir en mémoire.

Si vous déplacez régulièrement des grandes quantités de données à partir d’une base de données à une station de travail locale, au lieu de la requête la base de données à plusieurs reprises pour chaque opération de R, vous pouvez utiliser le fichier XDF pour enregistrer les données localement et ensuite utiliser dans votre espace de travail R, à l’aide du fichier XDF en tant que le cache.

+ `rxImport` -Déplacer les données d’une source ODBC dans le fichier XDF
+ `RxXdfData` -Permet de créer un objet de données XDF
+ `RxDataStep` -Lire les données de type int XDF une trame de données
+ `rxXdfToDataFrame` -Lire des données à partir de XDF dans une trame de données
+ `rxReadXdf` -Lit les données à partir de XDF dans une trame de données

Pour obtenir un exemple d’utilisation des fichiers XDF, consultez ce didacticiel :  [données Science immersion - utilisation des fonctions ScaleR](../../advanced-analytics/r-services/data-science-deep-dive-using-the-revoscaler-packages.md)

Pour plus d’informations sur ces fonctions ScaleR, qui peut être utilisé pour transférer des données de nombreuses sources différentes, consultez[ Microsoft R Server - mise en route](http://msdn.microsoft.com/microsoft-r/rserver/rserver-getting-started).

## Voir aussi
[Comparaison de Base R et ScaleR fonctions](https://msdn.microsoft.com/microsoft-r/scaler/compare-base-r-scaler-functions)
