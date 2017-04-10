---
title: "Le&#231;on&#160;10&#160;: Cr&#233;er des hi&#233;rarchies | Microsoft Docs"
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
ms.assetid: 1e2561d3-4890-4495-a9cd-84eb88508938
caps.latest.revision: 23
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Le&#231;on&#160;10&#160;: Cr&#233;er des hi&#233;rarchies
Dans cette leçon, vous allez créer des hiérarchies. Les hiérarchies sont des groupes de colonnes ordonnées par niveaux ; par exemple, une hiérarchie Geography peut avoir des sous-niveaux Country, State, County et City. Les hiérarchies peuvent apparaître séparément des autres colonnes dans une liste de champs de l'application cliente de création de rapports, ce qui les rend faciles à parcourir par les utilisateurs clients et à inclure dans un rapport. Pour plus d’informations, consultez [Hiérarchies &#40;SSAS Tabulaire&#41;](../analysis-services/tabular-models/hierarchies-ssas-tabular.md).  
  
Pour créer des hiérarchies, vous allez utiliser le concepteur de modèles dans la *Vue du diagramme*. La création et la gestion des hiérarchies n'est pas prise en charge dans le générateur de modèles dans la vue de données.  
  
Durée estimée pour effectuer cette leçon : **20 minutes**  
  
## Conditions préalables  
Cette rubrique fait partie d'un didacticiel de modélisation tabulaire, qui doit être suivi dans l'ordre. Avant d’effectuer les tâches de cette leçon, vous devez avoir terminé la leçon précédente : [Leçon 9 : Créer des perspectives](../Topic/Lesson%209:%20Create%20Perspectives.md).  
  
## Créer des hiérarchies  
  
#### Pour créer une hiérarchie de catégorie dans la table Product  
  
1.  Dans le concepteur de modèles, cliquez sur le menu **Modèle**, pointez sur **Vue du modèle**, puis cliquez sur **Vue de diagramme**.  
  
  
  
2.  Cliquez avec le bouton droit sur la table **Product**, puis cliquez sur **Créer une hiérarchie**. Une hiérarchie apparaît en bas de la fenêtre de la table.  
  
3.  Dans le nom de la hiérarchie, renommez la hiérarchie en tapant **Category**, puis appuyez sur Entrée.  
  
4.  Dans la table **Product**, cliquez sur la colonne **Product Category Name** et faites-la glisser sur la hiérarchie **Category**, en la relâchant sur **Category**.  
  
5.  Dans la hiérarchie **Category**, cliquez avec le bouton droit sur la colonne **Product Category Name**, puis cliquez sur **Renommer** et tapez **Category**.  
  
    > [!NOTE]  
    > Renommer une colonne dans une hiérarchie ne renomme pas cette colonne dans la table. Une colonne dans une hiérarchie est simplement une représentation de la colonne dans la table.  
  
6.  Dans la table **Product**, cliquez sur la colonne **Product Subcategory Name** et faites-la glisser vers la hiérarchie **Category**.  
  
7.  Renommez **Product Subcategory Name** en **Subcategory**.  
  
8.  Cliquez successivement sur les colonnes **Model Name** et **Product Name** et faites les glisser jusque sous la colonne **Product Subcategory Name**. Renommez ces colonnes en **Model** et **Product**, respectivement.  
  
#### Pour créer des hiérarchies dans la table Date  
  
1.  Dans le concepteur de modèles, cliquez avec le bouton droit sur la table **Date**, puis cliquez sur **Créer une hiérarchie**.  
  
2.  Renommez la hiérarchie en **Calendar**.  
  
3.  Ajoutez les colonnes suivantes, dans l'ordre, puis renommez-les :  
  
    |Colonne|Renommer en :|  
    |----------|--------------|  
    |Calendar Year|Année|  
    |Calendar Semester|Semester|  
    |Calendar Quarter|Quarter|  
    |Month Calendar|Mois|  
    |Day Of Month|Jour|  
  
4.  Dans la table **Date**, répétez les étapes ci-dessus, en créant une hiérarchie **Fiscal**, y compris les colonnes suivantes :  
  
    |Colonne|Renommer en :|  
    |----------|--------------|  
    |Fiscal Year|Année|  
    |Fiscal Semester|Semester|  
    |Fiscal Quarter|Quarter|  
    |Month Calendar|Mois|  
    |Day Of Month|Jour|  
  
5.  Enfin, dans la table **Date**, répétez les étapes ci-dessus, en créant une hiérarchie **Production Calendar**, comprenant les colonnes suivantes :  
  
    |Colonne|Renommer en :|  
    |----------|--------------|  
    |Calendar Year|Année|  
    |Week Number Of Year|Week|  
    |Jour de la semaine|Jour|  
  
## Étapes suivantes  
Pour poursuivre l’étude de ce didacticiel, passez à la [Leçon 11 : Créer des partitions](../analysis-services/lesson-11-create-partitions.md).  
  
  
  
