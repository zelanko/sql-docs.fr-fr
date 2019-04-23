---
title: Boîte de dialogue Propriétés du dataset, Options (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10020"
ms.assetid: 43e50133-45ef-47a2-b575-34dfcc28ec98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cbf7814d51fd0f726a60d3b177af18fbeba223d2
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59971285"
---
# <a name="dataset-properties-dialog-box-options-report-builder"></a>Boîte de dialogue Propriétés du dataset, Options (Générateur de rapports)
  Sélectionnez **Options** dans la boîte de dialogue **Propriétés du jeu de données** pour modifier les options de données, telles que les options de classement et le traitement des sous-totaux en tant que données de détail, pour la requête. Pour plus d’informations sur les classements, consultez [Prise en charge d’Unicode et du classement](../../relational-databases/collations/collation-and-unicode-support.md) dans la [documentation en ligne de SQL Server](https://go.microsoft.com/fwlink/?linkid=98335).  
  
 Les options de données qui font partie d'une définition de dataset partagé sur le serveur de rapports affectent tous les rapports qui utilisent le dataset partagé. Vous pouvez remplacer des options pour le dataset partagé après qu'il a été ajouté à un rapport. Ces modifications affectent uniquement le rapport dans lequel elles sont définies.  
  
 Les options de données d'un dataset incorporé affectent uniquement le rapport dans lequel elles sont définies.  
  
 Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Options  
 **Classement**  
 Sélectionnez des paramètres régionaux qui déterminent la séquence de classement du tri des données. **Par défaut** indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si cette valeur ne peut pas être dérivée, la valeur par défaut est dérivée à partir des paramètres régionaux en vigueur sur l'ordinateur.  
  
 **Respect de la casse**  
 Sélectionnez une valeur qui détermine le respect de la casse. Cette option indique si les données respectent la casse. Vous pouvez affecter les valeurs **True** , **False**ou **Auto**à l’option **Respect de la casse**. La valeur par défaut, **Auto**, indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect de la casse, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Respect des accents**  
 Sélectionnez une valeur qui détermine le respect des accents. L’option**Respect des accents** indique si les données respectent les accents ; elle peut prendre les valeurs **True**, **False**ou **Auto**. La valeur par défaut, **Auto**, indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect des accents, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Respect du jeu de caractères kana**  
 Sélectionnez une valeur qui détermine le respect du jeu de caractères kana. Cette option indique si les données respectent le jeu de caractères kana ; elle peut prendre les valeurs **True**, **False**ou **Auto**. La valeur par défaut, **Auto**, indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect du jeu de caractères kana, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Respect de la largeur**  
 Sélectionnez une valeur qui détermine le respect de la largeur. Cette option indique si les données respectent la largeur et peut prendre les valeurs **True**, **False**ou **Auto**. La valeur par défaut, **Auto**, indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect de la largeur, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Interpréter les sous-totaux comme des lignes de détails**  
 Sélectionnez une valeur qui indique si vous souhaitez que les lignes de sous-total soient interprétées comme des lignes de détails au lieu de lignes agrégées. La valeur par défaut, **automatique**, indique que les lignes de sous-total doivent être traitées comme des lignes de détail si le rapport n’utilise pas le `Aggregate`(fonction) () pour accéder aux champs du jeu de données. Si vous souhaitez que les lignes de sous-total soient interprétées comme lignes agrégées, choisissez **False**. Si vous souhaitez que les lignes de sous-total soient interprétées comme lignes de détails et que vous savez qu’elles n’utilisent pas le `Aggregate`() de fonction, choisissez **True**.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Fonction d’agrégation &#40;Générateur de rapports et SSRS&#41;](../report-design/report-builder-functions-aggregate-function.md)   
 [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Boîte de dialogue Propriétés du dataset, Requête &#40;Générateur de rapports&#41;](dataset-properties-dialog-box-query-report-builder.md)  
  
  
