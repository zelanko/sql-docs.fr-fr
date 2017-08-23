---
title: Mapper les colonnes dans des domaines composites | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9422412-8a3d-45ae-af7f-072c902a09ba
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8a8f24f9808d184229cb85be5ddc88d0102f2ee7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="map-columns-to-composite-domains"></a>Mapper des colonnes à des domaines composites
  Un domaine composite comprend deux ou plusieurs domaines uniques. Vous pouvez mapper plusieurs colonnes au domaine ou vous pouvez mapper une seule colonne de valeurs délimitées au domaine.  
  
 Lorsque vous avez plusieurs colonnes, vous devez mapper une colonne à chaque domaine unique du domaine composite pour appliquer les règles du domaine composite au nettoyage des données. Sélectionnez les domaines uniques contenus dans le domaine composite dans Data Quality Client. Pour plus d’informations, consultez [Créer un domaine composite](../../../data-quality-services/create-a-composite-domain.md).  
  
 Lorsque vous avez une seule colonne de valeurs délimitées, vous devez mapper la colonne unique au domaine composite. Les valeurs doivent apparaître dans le même ordre que celui dans lequel les domaines uniques apparaissent dans le domaine composite. Le délimiteur de la source de données doit correspondre à celui utilisé pour analyser les valeurs du domaine composite. Sélectionnez le délimiteur du domaine composite et définissez d'autres propriétés dans Data Quality Client. Pour plus d’informations, consultez [Créer un domaine composite](../../../data-quality-services/create-a-composite-domain.md).  
  
### <a name="to-map-multiple-columns-to-a-composite-domain"></a>Pour mapper plusieurs colonnes à un domaine composite  
  
1.  Cliquez avec le bouton droit sur la transformation de nettoyage DQS, puis sélectionnez **Modifier**.  
  
2.  Sous l’onglet **Gestionnaire de connexions** , vérifiez que le domaine composite apparaît dans la liste des domaines disponibles.  
  
3.  Sous l’onglet **Mappage** , sélectionnez les colonnes dans la zone **Colonnes d’entrée disponibles** .  
  
4.  Pour chaque colonne figurant dans le champ **Colonne d’entrée** , sélectionnez un domaine unique dans le champ **Domaine** . Sélectionnez uniquement des domaines uniques figurant dans le domaine composite.  
  
5.  Si nécessaire, modifiez les noms qui s’affichent dans les champs **Alias source**, **Alias de sortie**et **Alias d’état** .  
  
6.  Si nécessaire, définissez des propriétés sous l’onglet **Avancé** . Pour plus d’informations sur les propriétés, consultez [Éditeur de transformation de nettoyage DQS (boîte de dialogue)](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
### <a name="to-map-a-column-with-delimited-values-to-a-composite-domain"></a>Pour mapper une colonne de valeurs délimitées à un domaine composite  
  
1.  Cliquez avec le bouton droit sur la transformation de nettoyage DQS, puis sélectionnez **Modifier**.  
  
2.  Sous l’onglet **Gestionnaire de connexions** , vérifiez que le domaine composite apparaît dans la liste des domaines disponibles.  
  
3.  Sous l’onglet **Mappage** , sélectionnez la colonne dans la zone **Colonnes d’entrée disponibles** .  
  
4.  Pour la colonne figurant dans le champ **Colonne d’entrée** , sélectionnez le domaine composite dans le champ **Domaine** .  
  
5.  Si nécessaire, modifiez les noms qui s’affichent dans les champs **Alias source**, **Alias de sortie**et **Alias d’état** .  
  
6.  Si nécessaire, définissez des propriétés sous l’onglet **Avancé** . Pour plus d’informations sur les propriétés, consultez [Éditeur de transformation de nettoyage DQS (boîte de dialogue)](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation-editor-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de nettoyage DQS](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)  
  
  
