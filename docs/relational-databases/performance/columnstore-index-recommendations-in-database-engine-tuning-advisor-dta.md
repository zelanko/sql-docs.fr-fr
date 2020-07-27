---
title: Recommandations relatives aux index columnstore - DTA (Assistant Paramétrage du moteur de base de données)
description: Découvrez comment l’Assistant Paramétrage du moteur de base de données peut analyser votre charge de travail et vous recommander des index rowstore et columnstore à générer sur la base de données dans SQL Server.
ms.custom: seo-dt-2019
ms.date: 01/09/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Database Engine Tuning Advisor, columnstore index
- Database Engine Tuning Advisor, columnstore and rowstore indexes
ms.assetid: 9fba1139-82cb-4244-a41f-4337a7d0c132
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: f534e88529564f2fcb01c61911e291eaa7f99c30
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86457367"
---
# <a name="columnstore-index-recommendations-in-database-engine-tuning-advisor-dta"></a>Recommandations sur les index columnstore dans l’Assistant Paramétrage du moteur de base de données
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

 
  Les charges de travail d’analyse et d’entreposage des données (Data Warehouse) peuvent grandement profiter des [index columnstore](../../t-sql/statements/create-columnstore-index-transact-sql.md), ainsi que des index rowstore traditionnels. Le choix des index rowstore et columnstore à générer pour votre base de données dépend de la charge de travail de votre application. Dans SQL Server 2016, l’[Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md) peut analyser votre charge de travail et vous recommander une combinaison appropriée des index rowstore et columnstore à générer sur la base de données. 
  
 Cette fonctionnalité est disponible avec SQL Server Management Studio version **16.4** ou ultérieure. 
  
## <a name="how-to-enable-columnstore-index-recommendations-in-database-engine-tuning-advisor-gui"></a>Comment activer les recommandations relatives aux index columnstore dans l’interface graphique utilisateur de l’Assistant Paramétrage du moteur de base de données

  
  1. Lancez l’Assistant Paramétrage du moteur de base de données, puis ouvrez une nouvelle session de paramétrage.
  
  2. Dans le volet **Général**, sélectionnez une ou plusieurs bases de données et une charge de travail pour le paramétrage.
  
  3. Dans le volet Options de paramétrage, cochez la case **Index columnstore recommandés** (voir la figure ci-dessous).
  ![Option de paramétrage des index columnstore dans l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/media/dta-columnstore-indexes-tuning-option.gif)
 
  4. Sélectionnez d’autres options de paramétrage, puis cliquez sur le bouton **Démarrer l’analyse**.
  
  5. Une fois le paramétrage terminé, affichez toutes les recommandations, notamment les index columnstore, dans le volet **Recommandations** (voir la figure ci-dessous).      
  ![Recommandation d’index columnstore dans l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/media/dta-columnstore-index-recommendation.gif)
  
  6. Cliquez sur le lien hypertexte **Définition** pour afficher l’instruction DDL (Data Definition Language) SQL qui peut créer l’index recommandé. Par défaut, l’Assistant Paramétrage du moteur de base de données utilise le suffixe **col** dans le nom des index columnstore pour faciliter leur identification (voir la figure ci-dessous).
  ![Définition d’index columnstore dans l’Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/media/dta-columnstore-index-definition.gif) 
  
  
  ## <a name="how-to-enable-columnstore-index-recommendations-in-dtaexe-utility"></a>Comment activer les recommandations d’index columnstore dans l’utilitaire dta.exe

Pour activer les recommandations d’index columnstore quand vous utilisez l’utilitaire en ligne de commande dta.exe, utilisez le paramètre de ligne de commande  **-fc**.

Pour plus d’informations sur l’utilitaire de ligne de commande dta.exe, consultez [Utilitaire dta](../../tools/dta/dta-utility.md).

## <a name="see-also"></a>Voir aussi
[Guide des index columnstore](../../relational-databases/indexes/columnstore-indexes-overview.md)       
[Assistant Paramétrage du moteur de base de données](../../relational-databases/performance/database-engine-tuning-advisor.md)      
[Tutoriel : Assistant Paramétrage du moteur de base de données](../../tools/dta/tutorial-database-engine-tuning-advisor.md)



  

