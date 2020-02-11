---
title: Créer la stratégie Nom financier | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 56b2c852-fd69-4cd2-9b5d-977467b94fd9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a4484f9ccb76ea31c95a5392570e18df2c4b0ff5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67792916"
---
# <a name="create-the-finance-name-policy"></a>Créer la stratégie Nom financier
  Dans cette tâche, vous allez créer une base de données nommée finance, puis créer une condition qui exige que toutes les tables commencent par les lettres **fintbl**. Ensuite, vous allez créer une stratégie et une catégorie de stratégies afin d'appliquer une norme d'affectation de noms pour les tables dans la base de données Finance.  
  
### <a name="to-create-the-finance-database"></a>Pour créer la base de données Finance  
  
1.  Dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ouvrez une fenêtre de requête et exécutez l'instruction suivante :  
  
    ```  
    CREATE DATABASE Finance ;  
    GO  
    ```  
  
2.  Dans l’Explorateur d’objets, cliquez sur **Bases de données**, puis appuyez sur la touche F5 pour actualiser la liste de bases de données.  
  
### <a name="to-create-the-finance-tables-condition"></a>Pour créer la condition Tables de finance  
  
1.  Dans l’Explorateur d’objets, développez **Gestion**, **Gestion de la stratégie**, cliquez avec le bouton droit sur **Conditions**, puis cliquez sur **Nouvelle condition**.  
  
2.  Dans la boîte de dialogue **Créer une nouvelle condition** , dans la zone **Nom** , tapez **Tables de finance**.  
  
3.  Dans la liste **Facette** , sélectionnez **Nom en plusieurs parties**.  
  
4.  Dans la zone **expression** , dans la zone **champ** , sélectionnez ** \@nom**; dans la zone **opérateur** , sélectionnez **comme**; et dans la zone **valeur** , tapez **'fintbl% '** pour forcer tous les noms de tables à commencer par les lettres **fintbl**.  
  
5.  Dans la page **Description** , tapez **Les noms des tables de finance doivent commencer par fintbl**, puis cliquez sur **OK** pour créer la condition.  
  
### <a name="to-create-the-finance-name-policy"></a>Pour créer la stratégie Nom financier  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur **Stratégies**, puis cliquez sur **Nouvelle stratégie**.  
  
2.  Dans la boîte de dialogue **Créer une nouvelle stratégie** , dans la zone **Nom** , tapez **Nom financier**.  
  
3.  Dans la liste **Vérifier la condition** , sélectionnez **Tables de finance**. Cette zone se trouve dans la zone **Nom en plusieurs parties** .  
  
4.  Dans la zone **Par rapport à** est affichée une liste des objets de base de données qui pourraient appliquer cette stratégie. Cochez la case **Toutes les tables**.  
  
5.  Dans la zone **Toutes les bases de données** , développez **Toutes les**, puis cliquez sur **Nouvelle condition**.  
  
6.  Dans la boîte de dialogue **Créer une nouvelle condition** , dans la zone **Nom** , tapez **Base de données de finance**.  
  
7.  Dans la zone **expression** , complétez l’expression pour inclure ** \@Name = « finance »**, puis cliquez sur **OK** pour fermer la page de condition.  
  
    > [!NOTE]  
    >  Vous devrez peut-être quitter la zone **Valeur** pour activer le bouton **OK** .  
  
8.  Dans la liste **Mode d’évaluation** , sélectionnez **Sur modification : empêcher**. Cela applique la stratégie en créant un déclencheur de base de données sur la base de données Finance.  
  
9. Sélectionnez la liste **Activé** . (La case **Activé** ne s’applique pas aux stratégies **À la demande** .)  
  
10. Dans la liste **Restriction sur le serveur** , sélectionnez **Aucune**.  
  
11. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-create-the-finance-policy-category"></a>Pour créer la catégorie de stratégies Finance  
  
1.  Dans l’Explorateur d’objets, développez **Gestion**, cliquez avec le bouton droit sur **Gestion de la stratégie**, puis cliquez sur **Gérer les catégories**.  
  
2.  Dans la boîte de dialogue **gérer les catégories de stratégie** , sous `Finance` **nom**, tapez dans la zone vide, puis désactivez abonnements à la **base de données**autorisée. Les **abonnements de base de données mandat** forcent chaque base de données de l’instance à s’abonner aux stratégies appartenant à cette catégorie de stratégie. Dans le cadre de cette leçon, seule la base de données Finance doit s'abonner à la stratégie Nom financier.  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Vérifier et s'abonner à la stratégie Nom financier](lesson-2-2-subscribe-to-and-check-the-finance-name-policy.md)  
  
  
