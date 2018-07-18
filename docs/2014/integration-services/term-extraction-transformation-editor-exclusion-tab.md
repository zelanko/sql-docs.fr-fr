---
title: Éditeur de Transformation d’Extraction de terme (onglet Exclusion) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termextraction.inclusionexclusion.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 90110d95-fd97-4542-9cda-832c86606130
caps.latest.revision: 27
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 183814c58f867f0a9241d4dba1f01e96ee9b8982
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37246959"
---
# <a name="term-extraction-transformation-editor-exclusion-tab"></a>Éditeur de transformation d'extraction de terme (onglet Exclusion)
  Utilisez l'onglet **Exclusion** de la boîte de dialogue **Éditeur de transformation d'extraction de terme** pour définir une connexion à une table de connexion et les colonnes qui contiennent des termes d'exclusion.  
  
 Pour en savoir plus sur la transformation d'extraction de terme, consultez [Term Extraction Transformation](data-flow/transformations/term-extraction-transformation.md).  
  
## <a name="options"></a>Options  
 **Utiliser les termes d'exclusion**  
 Indique si vous voulez exclure des termes au cours de l'extraction de termes en définissant une colonne qui contient les termes d'exclusion. Vous devez définir les propriétés sources suivantes si vous choisissez d'exclure des termes.  
  
 **Gestionnaire de connexions OLE DB**  
 Sélectionnez un gestionnaire de connexions OLE DB existant ou créez une connexion en cliquant sur **Nouvelle**.  
  
 **Nouveau**  
 Créez une connexion à une base de données à l’aide de la boîte de dialogue **Configurer le Gestionnaire de connexions OLE DB** .  
  
 **Table ou vue**  
 Sélectionnez la table ou la vue qui contient les termes d'exclusion.  
  
 **Colonne**  
 Sélectionnez la colonne de la table ou de la vue qui contient les termes d'exclusion.  
  
 **Configurer la sortie d’erreur**  
 Utilisez la boîte de dialogue [Configurer l’affichage des erreurs](../../2014/integration-services/configure-error-output.md) pour spécifier la gestion des erreurs dans les lignes qui provoquent des erreurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de Transformation d’Extraction de terme &#40;onglet Extraction de terme&#41;](../../2014/integration-services/term-extraction-transformation-editor-term-extraction-tab.md)   
 [Éditeur de Transformation d’Extraction de terme &#40;onglet Avancé&#41;](../../2014/integration-services/term-extraction-transformation-editor-advanced-tab.md)   
 [Transformation de recherche de terme](data-flow/transformations/lookup-transformation.md)  
  
  
