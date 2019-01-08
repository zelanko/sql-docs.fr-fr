---
title: Créer et mapper un environnement serveur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.isenvprop.variables.f1
- sql12.ssis.ssms.iscreateenv.f1
- sql12.ssis.ssms.isenvprop.permissions.f1
- sql12.ssis.ssms.isenvprop.general.f1
ms.assetid: b1cbb697-713f-48e4-b234-b23724d87451
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1116cc2e1040326237a31039fa2b52618c3f559e
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52408226"
---
# <a name="create-and-map-a-server-environment"></a>Créer et mapper un environnement serveur
  Vous créez un environnement serveur pour spécifier les valeurs d’exécution des packages contenus dans un projet que vous avez déployé sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Vous pouvez ensuite mapper les variables d'environnement aux paramètres, pour un package spécifique, pour les packages de point d'entrée, ou pour tous les packages dans un projet donné. Un package de point d'entrée est généralement un package parent qui exécute un package enfant.  
  
> [!IMPORTANT]  
>  Pour une exécution données, un package peut s'exécuter uniquement avec les valeurs contenues dans un seul environnement.  
  
 Vous pouvez interroger les affichages afin d'obtenir la liste des environnements serveur, des références environnementales et des variables d'environnement. Vous pouvez également appeler des procédures stockées pour ajouter, supprimer et modifier des environnements, des références environnementales et des variables d'environnement. Pour plus d'informations, consultez la section **Environnements serveur, variables de serveur et références d'environnement serveur** dans [SSIS Catalog](catalog/ssis-catalog.md).  
  
### <a name="to-create-and-use-a-server-environment"></a>Pour créer et utiliser un environnement serveur  
  
1.  Dans [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], développez le nœud [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] Catalogues > **SSISDB** dans l’Explorateur d’objets, puis recherchez le dossier **Environnements** du projet pour lequel vous souhaitez créer un environnement.  
  
2.  Cliquez avec le bouton droit sur le dossier **Environnements**, puis cliquez sur **Créer l’environnement**.  
  
3.  Tapez un nom pour l'environnement, et éventuellement une description, puis cliquez sur **OK**.  
  
4.  Cliquez avec le bouton droit sur le nouvel environnement, puis sélectionnez **Propriétés**.  
  
5.  Dans la page **Variables** , procédez comme suit pour ajouter une variable.  
  
    1.  Sélectionnez le **Type** de la variable. Le nom de la variable ne doit **pas** nécessairement correspondre au nom du paramètre du projet que vous mappez à la variable.  
  
    2.  Entrez une **Description** facultative pour la variable.  
  
    3.  Entrez la **Valeur** de la variable d'environnement.  
  
         Pour plus d'informations sur les règles énoncées pour les noms de variable d'environnement, consultez la section **Variable d'environnement** dans [SSIS Catalog](catalog/ssis-catalog.md).  
  
    4.  Indiquez si la variable contient une valeur sensible, en activant ou désactivant la case à cocher **Sensible** .  
  
         Si vous sélectionnez **Sensible**, la valeur de la variable ne s'affiche pas dans le champ **Valeur** .  
  
         Les valeurs sensibles sont chiffrées dans le catalogue SSISDB. Pour plus d'informations sur le chiffrement, consultez [SSIS Catalog](catalog/ssis-catalog.md).  
  
6.  Dans la page **Autorisations** , accordez ou refusez des autorisations pour les rôles et les utilisateurs sélectionnés en procédant comme suit.  
  
    1.  Cliquez sur **Parcourir**, puis sélectionnez un ou plusieurs utilisateurs et rôles dans la boîte de dialogue **Parcourir tous les principaux** .  
  
    2.  Dans la zone **Connexions ou rôles** , sélectionnez l'utilisateur ou le rôle auquel vous souhaitez accorder ou refuser des autorisations.  
  
    3.  Dans la zone **Explicite** , cliquez sur **Accorder** ou sur **Refuser** en regard de chaque autorisation.  
  
7.  Pour générer un script de l'environnement, cliquez sur **Script**. Par défaut, le script s'affiche dans une nouvelle fenêtre de l'Éditeur de requête.  
  
    > [!TIP]  
    >  Vous devez cliquer sur **Script** après avoir apporté des modifications aux propriétés d’environnement, telles que l’ajout d’une variable, et avant de cliquer sur **OK** dans la boîte de dialogue **Propriétés d’environnement**. Sinon, aucun script n'est généré.  
  
8.  Cliquez sur **OK** pour enregistrer les propriétés de l'environnement.  
  
9. Sous le nœud **SSISDB** dans l’Explorateur d’objets, développez le dossier **Projets** , cliquez avec le bouton droit sur le projet, puis cliquez sur **Configurer**.  
  
10. Dans la page **Références** , cliquez sur **Ajouter** pour ajouter un environnement, puis cliquez sur **OK** pour enregistrer la référence dans l'environnement.  
  
11. Recliquez avec le bouton droit sur le projet, puis cliquez sur **Configurer**.  
  
12. Mappez la variable d'environnement à un paramètre que vous avez ajouté au package au moment de la conception, ou à un paramètre généré lors de la conversion du projet de [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] en modèle de déploiement de projet, procédez comme suit.  
  
    1.  Dans l'onglet **Paramètres** dans la page **Paramètres** , cliquez sur le bouton Parcourir en regard du champ **Valeur** .  
  
    2.  Cliquez sur **Utiliser la variable d'environnement**, puis sélectionnez la variable d'environnement que vous avez créée.  
  
13. Pour mapper la variable d'environnement à une propriété du gestionnaire de connexions, procédez comme suit. Les paramètres sont automatiquement générés sur le serveur SSIS pour les propriétés du gestionnaire de connexions.  
  
    1.  Dans l'onglet **Gestionnaires de connexions** dans la page **Paramètres** , cliquez sur le bouton Parcourir en regard du champ **Valeur** .  
  
    2.  Cliquez sur **Utiliser la variable d'environnement**, puis sélectionnez la variable d'environnement que vous avez créée.  
  
14. Cliquez deux fois sur **OK** pour enregistrer vos modifications.  
  
  
