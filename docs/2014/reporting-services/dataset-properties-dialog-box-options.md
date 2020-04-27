---
title: Boîte de dialogue Propriétés du DataSet, options | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10130"
- sql12.rtp.rptdesigner.datasetproperties.options.f1
ms.assetid: 95299049-71ba-427f-b723-775cb696243f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 778365e8fc7f40700b0f8c1683260f15c860a32a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66109408"
---
# <a name="dataset-properties-dialog-box-options"></a>Boîte de dialogue Propriétés du dataset, Options
  Sélectionnez **options** dans la boîte de dialogue **Propriétés** pour modifier les options de données, telles que les options de classement et les sous-totaux, pour la requête. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../relational-databases/collations/collation-and-unicode-support.md).  
  
## <a name="options"></a>Options  
 **Classement**  
 Sélectionnez des paramètres régionaux qui déterminent la séquence de classement du tri des données. **Par défaut** indique que le serveur de rapports doit tenter de dériver la valeur à partir du fournisseur de données, lors de l’exécution du rapport. Si cette valeur ne peut pas être dérivée, la valeur par défaut est dérivée à partir des paramètres régionaux en vigueur sur l'ordinateur.  
  
 **Respect de la casse**  
 Sélectionnez une valeur qui détermine le respect de la casse. Cette option indique si les données respectent la casse. Vous pouvez définir le **respect** de la casse sur **true**, **false**ou **auto**. La valeur par défaut, **auto**, indique que le serveur de rapports doit tenter de dériver la valeur du fournisseur de données lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect de la casse, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Respect des accents**  
 Sélectionnez une valeur qui détermine le respect des accents. **Respect des accents** indique si les données respectent les accents et peut avoir la valeur **true**, **false**ou **auto**. La valeur par défaut, **auto**, indique que le serveur de rapports doit tenter de dériver la valeur du fournisseur de données lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect des accents, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Respect du jeu de caractères kana**  
 Sélectionnez une valeur qui détermine le respect du jeu de caractères kana. Cette option indique si les données sont sensibles à la non ; elle peut avoir la valeur **true**, **false**ou **auto**. La valeur par défaut, **auto**, indique que le serveur de rapports doit tenter de dériver la valeur du fournisseur de données lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect du jeu de caractères kana, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Respect de la largeur**  
 Sélectionnez une valeur qui détermine le respect de la largeur. Cette option indique si les données respectent la largeur et peut avoir la valeur **true**, **false**ou **auto**. La valeur par défaut, **auto**, indique que le serveur de rapports doit tenter de dériver la valeur du fournisseur de données lors de l’exécution du rapport. Si le fournisseur de données ne prend pas en charge le type de respect de la largeur, le rapport s’exécute comme si la valeur était **False**. Si vous connaissez la valeur et savez qu’elle est prise en charge, choisissez **True**.  
  
 **Interpréter les sous-totaux comme des lignes de détails**  
 Sélectionnez une valeur qui indique si vous souhaitez que les lignes de sous-total soient interprétées comme des lignes de détails au lieu de lignes agrégées. La valeur par défaut, **auto**, indique que les lignes de sous-total doivent être traitées comme des lignes de détails si `Aggregate`le rapport n’utilise pas la fonction () pour accéder à tous les champs du jeu de données. Si vous souhaitez que les lignes de sous-total soient interprétées comme lignes agrégées, choisissez **False**. Si vous souhaitez que les lignes de sous-total soient interprétées comme des lignes de détails et que vous `Aggregate`sachiez qu’elles n’utilisent pas la fonction (), choisissez **true**.  
  
## <a name="see-also"></a>Voir aussi  
 [Définissez les paramètres régionaux d’un rapport ou d’une zone de texte &#40;Reporting Services&#41;](report-design/set-the-locale-for-a-report-or-text-box-reporting-services.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Nom de classement Windows &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql)   
 [Nom du classement SQL Server &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)   
 [Fonction d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-design/report-builder-functions-aggregate-function.md)  
  
  
