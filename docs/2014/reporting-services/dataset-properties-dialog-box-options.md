---
title: Boîte de dialogue Propriétés de DataSet, Options | Microsoft Docs
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
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66109408"
---
# <a name="dataset-properties-dialog-box-options"></a>Boîte de dialogue Propriétés du dataset, Options
  Sélectionnez **Options** sur le **DatasetProperties** boîte de dialogue pour modifier les options de données, telles que les options de classement et des sous-totaux, pour la requête. Pour plus d’informations, consultez [Prise en charge d’Unicode et du classement](../relational-databases/collations/collation-and-unicode-support.md).  
  
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
 [Définir les paramètres régionaux d’un rapport ou d’une zone de texte &#40;Reporting Services&#41;](report-design/set-the-locale-for-a-report-or-text-box-reporting-services.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Nom de classement Windows &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql)   
 [Nom du classement SQL Server &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql)   
 [Fonction d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-design/report-builder-functions-aggregate-function.md)  
  
  
