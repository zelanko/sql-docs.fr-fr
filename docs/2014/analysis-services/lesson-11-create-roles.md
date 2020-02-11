---
title: 'Leçon 12 : créer des rôles | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ec4bad8ef036e8f19ce0a856f3d9c04bafd0e7c5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079270"
---
# <a name="lesson-12-create-roles"></a>Leçon 12 : Créer des rôles
  Dans cette leçon, vous allez créer des rôles. Les rôles fournissent la sécurité des objets et des données d'une base de données de modèles, en limitant l'accès aux utilisateurs Windows qui y sont membres. Chaque rôle est défini avec une autorisation unique : aucune autorisation, autorisation de lecture, autorisation de lecture et de traitement, autorisation de traitement ou autorisation d’administrateur. Les rôles peuvent être définis lors de la création du modèle à l'aide de la boîte de dialogue Gestionnaire de rôles de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Une fois le modèle déployé, vous pouvez gérer les rôles à l'aide de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Rôles &#40;SSAS Tabulaire&#41;](tabular-models/roles-ssas-tabular.md).  
  
> [!NOTE]  
>  Il n’est pas nécessaire de créer des rôles pour suivre ce didacticiel. Par défaut, le compte avec lequel vous êtes actuellement connecté disposera de privilèges Administrateur sur le modèle. Toutefois, pour permettre à d'autres utilisateurs de votre organisation de parcourir le modèle à l'aide d'une application cliente de création de rapports, vous devez créer au moins un rôle avec des autorisations de lecture et ajouter ces utilisateurs en tant que membres.  
  
 Vous allez créer trois rôles :  
  
-   Responsable des ventes : ce rôle peut inclure les utilisateurs de votre organisation pour lesquels vous souhaitez disposer d’une autorisation de lecture sur tous les objets de modèle et données.  
  
-   Analyste des ventes-États-Unis : ce rôle peut inclure les utilisateurs de votre organisation pour lesquels vous souhaitez uniquement pouvoir parcourir les données relatives aux ventes aux États-Unis (États-Unis). Pour ce rôle, vous allez utiliser une formule DAX de façon à définir un *filtre de lignes*, qui limite les membres à parcourir uniquement les données concernant les États-Unis.  
  
-   Administrateur : ce rôle peut inclure des utilisateurs pour lesquels vous souhaitez disposer d’une autorisation d’administrateur, qui permet un accès et des autorisations illimités pour effectuer des tâches d’administration sur la base de données model.  
  
 Étant donné que les comptes d’utilisateurs et de groupes Windows de votre organisation sont uniques, vous pouvez ajouter des comptes de votre organisation spécifique aux membres. Toutefois, pour ce didacticiel, vous pouvez également laisser les membres vides. Vous pourrez toujours tester l’effet de chaque rôle ultérieurement dans la leçon 12 : Analyser dans Excel.  
  
 Durée estimée pour suivre cette leçon : **15 minutes**  
  
## <a name="prerequisites"></a>Conditions préalables requises  
 Cette rubrique fait partie d’un didacticiel de modélisation tabulaire, qui doit être suivi dans l’ordre prévu. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la [Leçon 11 : Créer des partitions](lesson-10-create-partitions.md).  
  
## <a name="create-roles"></a>Créer les rôles  
  
#### <a name="to-create-a-sales-manager-user-role"></a>Pour créer un rôle d’utilisateur Sales Manager (Responsable des ventes)  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Rôles**.  
  
2.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
     Un nouveau rôle avec l’autorisation Aucune est ajouté à la liste.  
  
3.  Cliquez sur le nouveau rôle, puis dans la colonne **nom** , renommez le rôle `Internet Sales Manager`.  
  
4.  Dans la colonne **Autorisations**, cliquez sur la liste déroulante et sélectionnez l’autorisation **Lecture**.  
  
5.  Facultatif : Cliquez sur l’onglet **Membres**, puis sur **Ajouter**.  
  
6.  Dans la boîte de dialogue **Sélectionner des utilisateurs ou des groupes**, entrez les utilisateurs ou les groupes Windows de votre organisation à inclure dans le rôle.  
  
7.  Vérifiez vos sélections, puis cliquez sur **OK** .  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>Pour créer un rôle d’utilisateur Sales Analyst US (Analyste en ventes aux États-Unis)  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Rôles**.  
  
2.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
     Un nouveau rôle avec l’autorisation Aucune est ajouté à la liste.  
  
3.  Cliquez sur le nouveau rôle, puis dans la colonne **nom** , renommez le rôle `Internet Sales US`.  
  
4.  Dans la colonne **Autorisations**, cliquez sur la liste déroulante et sélectionnez l’autorisation **Lecture**.  
  
5.  Cliquez sur l’onglet Filtres de lignes puis, pour la table **Geography** uniquement, dans la colonne Filtre DAX, tapez la formule suivante :  
  
     `=Geography[Country Region Code] = "US"`  
  
     Une formule de filtre de lignes doit être résolue en une valeur booléenne (TRUE/FALSE). Avec cette formule, vous spécifiez que seules les lignes avec la valeur de code Country Region « US » sont visibles par l’utilisateur.  
  
     Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
6.  Facultatif : Cliquez sur l’onglet **Membres**, puis sur **Ajouter**.  
  
7.  Dans la boîte de dialogue **Sélectionner des utilisateurs ou des groupes**, entrez les utilisateurs ou les groupes Windows de votre organisation à inclure dans le rôle.  
  
8.  Vérifiez vos sélections, puis cliquez sur **OK** .  
  
#### <a name="to-create-an-administrator-role"></a>Pour créer un rôle d'administrateur  
  
1.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
2.  Cliquez sur le nouveau rôle, puis dans la colonne **nom** , renommez le rôle `Internet Sales Administrator`.  
  
3.  Dans la colonne **Autorisations** , cliquez sur la liste déroulante, puis sélectionnez l’autorisation **Administrateur** .  
  
4.  Cliquez sur l’onglet **Membres** , puis cliquez sur **Ajouter**.  
  
5.  Facultatif : dans la boîte de dialogue **Sélectionner des utilisateurs ou des groupes** , entrez les utilisateurs ou les groupes Windows de votre organisation à inclure dans le rôle.  
  
6.  Vérifiez vos sélections, puis cliquez sur **OK** .  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour continuer ce didacticiel, passez à la leçon suivante : [Leçon 13 : Analyser dans Excel](lesson-12-analyze-in-excel.md).  
  
  
