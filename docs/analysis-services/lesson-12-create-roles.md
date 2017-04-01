---
title: "Le&#231;on&#160;12&#160;: Cr&#233;er des r&#244;les | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Le&#231;on&#160;12&#160;: Cr&#233;er des r&#244;les
Dans cette leçon, vous allez créer des rôles. Les rôles fournissent la sécurité des objets et des données d'une base de données de modèles, en limitant l'accès aux utilisateurs Windows qui y sont membres. Chaque rôle est défini avec une autorisation unique : aucune autorisation, autorisation de lecture, autorisation de lecture et traitement, autorisation de traitement ou autorisation d'administrateur. Les rôles peuvent être définis lors de la création du modèle à l'aide de la boîte de dialogue Gestionnaire de rôles de [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]. Une fois le modèle déployé, vous pouvez gérer les rôles à l'aide de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Pour plus d’informations, consultez [Rôles &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/roles-ssas-tabular.md).  
  
> [!NOTE]  
> La création de rôles n'est pas nécessaire pour effectuer ce didacticiel. Par défaut, le compte auquel vous êtes connecté aura des privilèges d'administrateur sur le modèle. Toutefois, pour permettre à d'autres utilisateurs de votre organisation de parcourir le modèle à l'aide d'une application cliente de création de rapports, vous devez créer au moins un rôle avec des autorisations de lecture et ajouter ces utilisateurs en tant que membres.  
  
Vous allez créer trois rôles :  
  
-   Sales Manager (Responsable des ventes) - Ce rôle peut inclure les utilisateurs de votre organisation auxquels vous souhaitez donner un accès en lecture à tous les objets et données du modèle.  
  
-   Sales Analyst US (Analyste en ventes aux États-Unis) - Ce rôle peut inclure des utilisateurs de votre organisation auxquels vous souhaitez uniquement donner accès aux données relatives aux ventes aux États-Unis. Pour ce rôle, vous utilisez une formule DAX pour définir un *filtre de lignes*, qui limite l’accès des membres aux seules données concernant les États-Unis.  
  
-   Administrateur - Ce rôle peut inclure des utilisateurs auxquels vous souhaitez fournir une autorisation d'administrateur, qui permet un accès et des autorisations illimités pour effectuer des tâches administratives sur la base de données de modèles.  
  
Étant donné que les comptes d'utilisateurs et de groupes Windows dans votre organisation sont uniques, vous pouvez ajouter des comptes de votre organisation aux membres. Toutefois, pour ce didacticiel, vous pouvez également laissez les membres vides. Vous pourrez toujours tester l'effet de chaque rôle plus loin dans la leçon 12 : analyser dans Excel.  
  
Durée estimée pour effectuer cette leçon : **15 minutes**  
  
## Conditions préalables  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 11 : Créer des partitions](../analysis-services/lesson-11-create-partitions.md).  
  
## Créer les rôles  
  
#### Pour créer un rôle d'utilisateur Sales Manager  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle**, puis sur **Rôles**.  
  
2.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
    Un nouveau rôle sans aucune autorisation est ajouté à la liste.  
  
3.  Cliquez sur le nouveau rôle puis, dans la colonne **Nom**, renommez le rôle en **Internet Sales Manager**.  
  
4.  Dans la colonne **Autorisations**, cliquez sur la liste déroulante, puis sélectionnez l’autorisation **Lecture**.  
  
5.  Facultatif : cliquez sur l’onglet **Membres**, puis cliquez sur **Ajouter**.  
  
6.  Dans la boîte de dialogue **Sélectionner des utilisateurs ou des groupes**, entrez les utilisateurs ou les groupes Windows de votre organisation à inclure dans le rôle.  
  
7.  Vérifiez vos sélections, puis cliquez sur **OK**.  
  
#### Pour créer un rôle d'utilisateur Sales Analyst US  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle**, puis sur **Rôles**.  
  
2.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
    Un nouveau rôle sans aucune autorisation est ajouté à la liste.  
  
3.  Cliquez sur le nouveau rôle puis, dans la colonne **Nom**, renommez le rôle en **Internet Sales US**.  
  
4.  Dans la colonne **Autorisations**, cliquez sur la liste déroulante, puis sélectionnez l’autorisation **Lecture**.  
  
5.  Cliquez sur l’onglet Filtres de lignes puis, pour la table **Geography** uniquement, dans la colonne Filtre DAX, tapez la formule suivante :  
  
    **=Geography[Country Region Code] = "US"**  
  
    Une formule de filtre de lignes doit être résolue en une valeur booléenne (TRUE/FALSE). Avec cette formule, vous spécifiez que seules les lignes avec la valeur Country Region Code « US » sont visibles pour l'utilisateur.  
  
    Lorsque vous avez terminé de générer la formule, appuyez sur ENTRÉE pour l'accepter.  
  
6.  Facultatif : cliquez sur l’onglet **Membres**, puis cliquez sur **Ajouter**.  
  
7.  Dans la boîte de dialogue **Sélectionner des utilisateurs ou des groupes**, entrez les utilisateurs ou les groupes Windows de votre organisation à inclure dans le rôle.  
  
8.  Vérifiez vos sélections, puis cliquez sur **OK**.  
  
#### Pour créer un rôle d'administrateur  
  
1.  Dans la boîte de dialogue **Gestionnaire de rôles** , cliquez sur **Nouveau**.  
  
2.  Cliquez sur le nouveau rôle puis, dans la colonne **Nom**, renommez le rôle en **Internet Sales Administrator**.  
  
3.  Dans la colonne **Autorisations**, cliquez sur la liste déroulante, puis sélectionnez l’autorisation **Administrateur**.  
  
4.  Cliquez sur l’onglet **Membres**, puis cliquez sur **Ajouter**.  
  
5.  Facultatif : dans la boîte de dialogue **Sélectionner des utilisateurs ou des groupes**, entrez les utilisateurs ou les groupes Windows de votre organisation à inclure dans le rôle.  
  
6.  Vérifiez vos sélections, puis cliquez sur **OK**.  
  
## Étapes suivantes  
Pour continuer ce didacticiel, passez à la leçon suivante : [Leçon 13 : Analyser dans Excel](../analysis-services/lesson-13-analyze-in-excel.md).  
  
  
  
