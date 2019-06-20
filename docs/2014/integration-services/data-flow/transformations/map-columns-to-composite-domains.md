---
title: Mapper des colonnes à des domaines composites | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: d9422412-8a3d-45ae-af7f-072c902a09ba
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9ce189688bd33f3cb63280e4fa44bb2284ee9e8d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62900035"
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
  
6.  Si nécessaire, définissez des propriétés sous l’onglet **Avancé** . Pour plus d’informations sur les propriétés, consultez [Éditeur de transformation de nettoyage DQS (boîte de dialogue)](../../dqs-cleansing-transformation-editor-dialog-box.md).  
  
### <a name="to-map-a-column-with-delimited-values-to-a-composite-domain"></a>Pour mapper une colonne de valeurs délimitées à un domaine composite  
  
1.  Cliquez avec le bouton droit sur la transformation de nettoyage DQS, puis sélectionnez **Modifier**.  
  
2.  Sous l’onglet **Gestionnaire de connexions** , vérifiez que le domaine composite apparaît dans la liste des domaines disponibles.  
  
3.  Sous l’onglet **Mappage** , sélectionnez la colonne dans la zone **Colonnes d’entrée disponibles** .  
  
4.  Pour la colonne figurant dans le champ **Colonne d’entrée** , sélectionnez le domaine composite dans le champ **Domaine** .  
  
5.  Si nécessaire, modifiez les noms qui s’affichent dans les champs **Alias source**, **Alias de sortie**et **Alias d’état** .  
  
6.  Si nécessaire, définissez des propriétés sous l’onglet **Avancé** . Pour plus d’informations sur les propriétés, consultez [Éditeur de transformation de nettoyage DQS (boîte de dialogue)](../../dqs-cleansing-transformation-editor-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de nettoyage DQS](dqs-cleansing-transformation.md)  
  
  
