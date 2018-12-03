---
title: 'Leçon 1 : Créer et appliquer une stratégie Désactivé par défaut | Microsoft Docs'
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: security
ms.prod_service: database-engine
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: d31367db-b7db-44c4-8df2-f1240474cf78
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 678f9da12655cc733dcdf95aca5f61e5aa1cd45e
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158620"
---
# <a name="lesson-1-create-and-apply-an-off-by-default-policy"></a>Leçon 1 : Créer et appliquer une stratégie Désactivé par défaut
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
À l'aide des stratégies de la Gestion basée sur des stratégies, vous pouvez administrer une ou plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], un ou plusieurs objets d'instance, une ou plusieurs instances de serveur, une ou plusieurs bases de données, de même qu'un ou plusieurs objets de base de données. En tant qu'administrateur de base de données, vous souhaitez vous assurer que la Messagerie de base de données n'est pas activée sur certains serveurs. Dans cette leçon, vous allez créer une condition et une stratégie qui définissent cette option de serveur. Vous allez tester le serveur pour vérifier s'il est conforme à la stratégie. Ensuite, vous utiliserez la stratégie pour reconfigurer le serveur afin de le rendre conforme.  

## <a name="prerequisites"></a>Conditions préalables requises
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio et d’un accès à un serveur qui exécute SQL Server. 

- Installez [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/sql-server/sql-server-downloads).
  
## <a name="create-the-mail-off-condition"></a>Créer la condition mail-off

1.  Dans l’Explorateur d’objets, développez **Gestion**, **Gestion de la stratégie**, **Facettes**, cliquez avec le bouton droit sur **Configuration de la surface d’exposition**, puis cliquez sur **Nouvelle condition**.  

    ![nouvelle condition](Media/lesson-1-create-and-apply-an-off-by-default-policy/new-surface-area-condition.png)
  
2.  Dans la boîte de dialogue **Créer une nouvelle condition** , dans la zone **Nom** , tapez **Mail Off**.   
    1. Dans la zone **Facette** , vérifiez que la facette **Configuration de la surface d’exposition** est sélectionnée.
    1. Dans la boîte de dialogue **Expression** , dans la zone **Champ** , sélectionnez **@DatabaseMailEnabled**; ensuite, dans la zone **Opérateur** , sélectionnez **=**; enfin, dans **Valeur** , sélectionnez **Faux**.  
    1. Dans la page **Description** , entrez une description de la condition, puis cliquez sur **OK** pour créer la condition.  

    ![Condition mail-off](Media/lesson-1-create-and-apply-an-off-by-default-policy/mail-off-condition.png) 
  
## <a name="create-the-off-by-default-policy"></a>Créer la stratégie off-by-default  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur **Configuration de la surface d’exposition**, puis cliquez sur **Nouvelle stratégie**.  
  
2.  Dans la boîte de dialogue **Créer une nouvelle stratégie** , dans la zone **Nom** , tapez **Off By Default**. 
    1. Laissez la case **Activé** décochée. La case à cocher **Activé** s’applique aux stratégies automatisées ; cette stratégie sera exécutée à la demande.
    1. Dans la case à cocher **Vérifier la condition** , faites défiler la liste jusqu’à la zone **Configuration de la surface d’exposition** , puis sélectionnez **Mail Off** comme condition à vérifier.
    1. La zone **Par rapport aux cibles** est vide car il s’agit d’une stratégie dont l’étendue est le serveur. 
    1. Dans la case à cocher **Mode d’évaluation** , sélectionnez **À la demande** .
    1. Dans la case à cocher **Restriction sur le serveur** , sélectionnez **Aucune**.
    1. Dans la page **Description** , tapez une description de la stratégie.  

    ![Stratégie off by default](Media/lesson-1-create-and-apply-an-off-by-default-policy/off-by-default-policy.png)
  
9. Dans la page de description, vous pouvez fournir un lien hypertexte vers une page web pour vos stratégies dans la zone **Lien hypertexte d’aide supplémentaire**. Dans la zone **Texte à afficher** , tapez le texte du lien hypertexte.
    1. Dans la zone **Adresse** , tapez un lien hypertexte vers une page d’aide, par exemple la page d’accueil du service informatique de votre société.
    1. Pour vérifier l’adresse en ouvrant la page web, cliquez sur **Lien de test**.
    1. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

    ![Lien web de la stratégie off-by-default](Media/lesson-1-create-and-apply-an-off-by-default-policy/off-by-default-policy-web-link.png)


## <a name="configure-server-to-run-off-by-default-policy"></a>Configurer un serveur pour exécuter la stratégie off-by-default 

1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], pointez sur **Stratégies**, puis cliquez sur **Évaluer**.  

    ![évaluer une stratégie](Media/lesson-1-create-and-apply-an-off-by-default-policy/evaluate-policy.png)
  
2.  Dans la boîte de dialogue **Évaluer les stratégies** , vous pouvez sélectionner des stratégies à partir d’une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou d’un fichier. Pour cette étape, laissez le paramètre **Source** défini à votre instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
    1. Dans la section **Stratégies** , sélectionnez la stratégie **Désactivé par défaut** .
    1. Pour voir si le serveur est conforme à la stratégie, cliquez sur **Évaluer**.
    1. Dans la zone **Résultats** , vous verrez un cercle vert avec une coche si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] est conforme à la stratégie. Vous verrez un cercle rouge avec un X si le [!INCLUDE[ssDE](../../includes/ssde-md.md)] n'est pas conforme à la stratégie. 

   ![Évaluer la stratégie off-by-default](Media/lesson-1-create-and-apply-an-off-by-default-policy/evaluate-off-by-default-policy.png)

  
6.  Dans la zone **Détails sur les cibles** , des informations supplémentaires apparaîtront dans la colonne **Message** si une erreur se produit. Dans la colonne **Message** , cliquez sur **Afficher** pour voir un rapport contenant les résultats de la vérification de chaque propriété de facette. 

    ![Voir les résultats de l’évaluation de la stratégie ](Media/lesson-1-create-and-apply-an-off-by-default-policy/view-results-of-policy-evaluation.png)
  
7.  La description de stratégie est affichée en bas de la page et la section **Aide supplémentaire** affiche le lien hypertexte que vous avez configuré pour la stratégie. Cliquez sur le lien hypertexte pour ouvrir la page Web que vous avez spécifiée lors de la création de la stratégie.   

1.  Fermez le navigateur, puis fermez la boîte de dialogue **Vue détaillée des résultats** .  

1. Si le serveur n’est pas conforme et que vous souhaitez désactiver la messagerie de base de données, cliquez sur **Appliquer** dans la page **Résultats d’évaluation** .  
  
10. Fermez les boîtes de dialogue **Vue détaillée des résultats** et **Évaluer les stratégies** .   

   
## <a name="next-lesson"></a>Leçon suivante  
[Leçon 2 : Créer et appliquer une stratégie de normes d'affectation de noms](../../relational-databases/policy-based-management/lesson-2-create-and-apply-a-naming-standards-policy.md)  
  
  
  
