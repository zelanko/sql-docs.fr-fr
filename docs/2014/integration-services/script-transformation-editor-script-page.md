---
title: Éditeur de Transformation de script (Page Script) | Microsoft Docs
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
- sql12.dts.designer.scriptcomponent.script.f1
helpviewer_keywords:
- Script Transformation Editor
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
caps.latest.revision: 37
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: f620afb4ab4e32776d36ad5a1f37fd6ad28f3644
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37217649"
---
# <a name="script-transformation-editor-script-page"></a>Éditeur de transformation de script (page Script)
  Utilisez l'onglet **Script** de la boîte de dialogue **Éditeur de transformation de script** pour définir un script et les propriétés associées.  
  
 Pour en savoir plus sur le composant de script, consultez [Script Component](data-flow/transformations/script-component.md) et [Configuring the Script Component in the Script Component Editor](extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Pour en savoir plus sur la programmation du composant de script, consultez [Extending the Data Flow with the Script Component](extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## <a name="options"></a>Options  
 **Propriétés**  
 Affichez et modifiez les propriétés de la transformation de script. La plupart des propriétés affichées sont en lecture seule. Vous pouvez modifier les propriétés suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Description**|Décrit la transformation de script en terme de fonction.|  
|**LocaleID**|Définissez les paramètres régionaux pour fournir des informations spécifiques à la région relatives au tri et à la conversion de date et d'heure.|  
|**Nom**|Entrez un nom descriptif pour le composant.|  
|**ValidateExternalMetadata**|Indiquez si la transformation de script valide les métadonnées de colonne par rapport aux sources de données externes lors de la conception. La valeur `false` diffère la validation jusqu'à moment de l’exécution.|  
|**ReadOnlyVariables**|Tapez une liste de variables séparées par une virgule pour l'accès en lecture seule par la transformation de script.<br /><br /> Remarque : les noms des variables respectent la casse.|  
|**ReadWriteVariables**|Tapez une liste de variables séparées par une virgule pour l'accès en lecture/écriture par la transformation de script.<br /><br /> Remarque : les noms des variables respectent la casse.|  
|**ScriptLanguage**|Sélectionnez le langage de script que le composant de script doit utiliser.<br /><br /> Pour définir le langage de script par défaut pour les composants et les tâches de script, utilisez l'option **Langage de script** dans la page **Général** de la boîte de dialogue **Options** . Pour plus d'informations, consultez [General Page](general-page-of-integration-services-designers-options.md).|  
|**UserComponentTypeName**|Spécifie la classe <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> et l'assembly `Microsoft.SqlServer.TxScript` qui prennent en charge l'infrastructure [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
  
 **Modifier le script**  
 Utilisez [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tools for Applications (VSTA) pour créer ou modifier un script.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Sélectionner le Type de composant de Script](../../2014/integration-services/select-script-component-type.md)   
 [Éditeur de Transformation de script &#40;Page de colonnes d’entrée&#41;](../../2014/integration-services/script-transformation-editor-input-columns-page.md)   
 [Éditeur de Transformation de script &#40;entrées et de sorties de Page&#41;](../../2014/integration-services/script-transformation-editor-inputs-and-outputs-page.md)   
 [Éditeur de Transformation de script &#40;Page gestionnaires de connexions&#41;](../../2014/integration-services/script-transformation-editor-connection-managers-page.md)   
 [Exemples supplémentaires du composant Script](extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  
