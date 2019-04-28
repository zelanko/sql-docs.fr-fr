---
title: 'Leçon 12 : Créer des rôles | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4eec5e4f93a085ab784135593c139410f5911e1e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62729616"
---
# <a name="lesson-12-create-roles"></a>Leçon 12 : Créer les rôles
  Dans cette leçon, vous allez créer des rôles. Les rôles fournissent la sécurité des objets et des données d'une base de données de modèles, en limitant l'accès aux utilisateurs Windows qui y sont membres. Chaque rôle est défini avec une autorisation unique : Aucun, lecture, lecture et processus, processus ou administrateur. Les rôles peuvent être définis lors de la création du modèle à l'aide de la boîte de dialogue Gestionnaire de rôles de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Une fois le modèle déployé, vous pouvez gérer les rôles à l'aide de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Rôles &#40;SSAS Tabulaire&#41;](tabular-models/roles-ssas-tabular.md).  
  
> [!NOTE]  
>  La création de rôles n'est pas nécessaire pour effectuer ce didacticiel. Par défaut, le compte auquel vous êtes connecté aura des privilèges d'administrateur sur le modèle. Toutefois, pour permettre à d'autres utilisateurs de votre organisation de parcourir le modèle à l'aide d'une application cliente de création de rapports, vous devez créer au moins un rôle avec des autorisations de lecture et ajouter ces utilisateurs en tant que membres.  
  
 Vous allez créer trois rôles :  
  
-   Responsable des ventes - ce rôle peut inclure des utilisateurs dans votre organisation pour laquelle vous souhaitez avoir accès en lecture à tous les objets de modèle et les données.  
  
-   Analyste des ventes États-Unis - ce rôle peut inclure des utilisateurs dans votre organisation pour laquelle vous souhaitez uniquement être en mesure de parcourir les données relatives aux ventes aux États-Unis (United States). Pour ce rôle, vous utilisez une formule DAX pour définir un *filtre de lignes*, qui limite l’accès des membres aux seules données concernant les États-Unis.  
  
-   Administrateur - ce rôle peut inclure des utilisateurs pour lesquels vous souhaitez disposer de droits d’administrateur, ce qui permet un accès illimité et autorisations pour effectuer des tâches d’administration sur la base de données model.  
  
 Étant donné que les comptes d'utilisateurs et de groupes Windows dans votre organisation sont uniques, vous pouvez ajouter des comptes de votre organisation aux membres. Toutefois, pour ce didacticiel, vous pouvez également laissez les membres vides. Vous serez toujours en mesure de tester l’effet de chaque rôle ultérieurement dans la leçon 12 : Analyser dans Excel.  
  
 Durée estimée pour effectuer cette leçon : **15 minutes**  
  
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 11 : Créer des Partitions](lesson-10-create-partitions.md).  
  
## <a name="create-roles"></a>Créer les rôles  
  
#### <a name="to-create-a-sales-manager-user-role"></a>Pour créer un rôle d'utilisateur Sales Manager  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Rôles**.  
  
2.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
     Un nouveau rôle sans aucune autorisation est ajouté à la liste.  
  
3.  Cliquez sur le nouveau rôle, puis dans le **nom** colonne, renommez le rôle en `Internet Sales Manager`.  
  
4.  Dans la colonne **Autorisations** , cliquez sur la liste déroulante, puis sélectionnez l’autorisation **Lecture** .  
  
5.  Facultatif : Cliquez sur l’onglet **Membres** , puis cliquez sur **Ajouter**.  
  
6.  Dans la boîte de dialogue **Sélectionner des utilisateurs ou des groupes** , entrez les utilisateurs ou les groupes Windows de votre organisation à inclure dans le rôle.  
  
7.  Vérifiez vos sélections, puis cliquez sur **OK**.  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>Pour créer un rôle d'utilisateur Sales Analyst US  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Rôles**.  
  
2.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
     Un nouveau rôle sans aucune autorisation est ajouté à la liste.  
  
3.  Cliquez sur le nouveau rôle, puis dans le **nom** colonne, renommez le rôle en `Internet Sales US`.  
  
4.  Dans la colonne **Autorisations** , cliquez sur la liste déroulante, puis sélectionnez l’autorisation **Lecture** .  
  
5.  Cliquez sur l’onglet Filtres de lignes puis, pour la table **Geography** uniquement, dans la colonne Filtre DAX, tapez la formule suivante :  
  
     `=Geography[Country Region Code] = "US"`  
  
     Une formule de filtre de lignes doit être résolue en une valeur booléenne (TRUE/FALSE). Avec cette formule, vous spécifiez que seules les lignes avec la valeur Code pays / région « US » soit visible par l’utilisateur.  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
6.  Facultatif : Cliquez sur l’onglet **Membres** , puis cliquez sur **Ajouter**.  
  
7.  Dans la boîte de dialogue **Sélectionner des utilisateurs ou des groupes** , entrez les utilisateurs ou les groupes Windows de votre organisation à inclure dans le rôle.  
  
8.  Vérifiez vos sélections, puis cliquez sur **OK**.  
  
#### <a name="to-create-an-administrator-role"></a>Pour créer un rôle d'administrateur  
  
1.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
2.  Cliquez sur le nouveau rôle, puis dans le **nom** colonne, renommez le rôle en `Internet Sales Administrator`.  
  
3.  Dans la colonne **Autorisations** , cliquez sur la liste déroulante, puis sélectionnez l’autorisation **Administrateur** .  
  
4.  Cliquez sur l’onglet **Membres** , puis cliquez sur **Ajouter**.  
  
5.  Facultatif : Dans la boîte de dialogue **Sélectionner des utilisateurs ou des groupes** , entrez les utilisateurs ou les groupes Windows de votre organisation à inclure dans le rôle.  
  
6.  Vérifiez vos sélections, puis cliquez sur **OK**.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour continuer ce didacticiel, passez à la leçon suivante : Leçon : [Leçon 13 : Analyser dans Excel](lesson-12-analyze-in-excel.md).  
  
  
