---
title: Sélectionner une table et des clés de dimension (Assistant Dimension à variation lente) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.loaddimwizard.selecttableandkeys.f1
ms.assetid: 01e0495f-de35-4607-ba19-0539e801e8fd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7f93d60b28488dbb910dcb727015c25848db220e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62770445"
---
# <a name="select-a-dimension-table-and-keys-slowly-changing-dimension-wizard"></a>Sélectionner une table et des clés de dimension (Assistant Dimension à variation lente)
  Utilisez la page **Sélectionner une table et des clés de dimension** pour sélectionner une table de dimension à charger. Mappez les colonnes du flux de données avec les colonnes qui vont être chargées.  
  
 Pour en savoir plus sur cet Assistant, consultez [Slowly Changing Dimension Transformation](slowly-changing-dimension-transformation.md).  
  
## <a name="options"></a>Options  
 **Connection manager**  
 Sélectionnez un gestionnaire de connexions OLE DB existant dans la liste ou cliquez sur **Nouveau** pour créer un gestionnaire de connexions OLE DB.  
  
> [!NOTE]  
>  L’Assistant Dimension à variation lente prend en charge les gestionnaires de connexions OLE DB et prend uniquement en charge les connexions à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 **Nouveau**  
 Utilisez la boîte de dialogue **Configurer le gestionnaire de connexions OLE DB** pour sélectionner un gestionnaire de connexions existant ou cliquez sur **Nouvelle** pour créer une nouvelle connexion OLE DB.  
  
 **Table ou vue**  
 Sélectionnez une table ou une vue dans la liste.  
  
 **Colonnes d'entrée**  
 Sélectionnez dans la liste les colonnes d'entrée auxquelles vous voulez appliquer le mappage.  
  
 **Colonnes de dimension**  
 Affiche toutes les colonnes de dimension disponibles.  
  
 **Type de clé**  
 Sélectionnez la colonne de dimension qui sera la clé d'entreprise. Vous devez avoir une clé d'entreprise.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les sorties à l'aide de l'Assistant Dimension à variation lente](configure-outputs-using-the-slowly-changing-dimension-wizard.md)  
  
  
