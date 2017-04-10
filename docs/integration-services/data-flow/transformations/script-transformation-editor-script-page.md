---
title: "&#201;diteur de transformation de script (page Script) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.scriptcomponent.script.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de script"
ms.assetid: 4c6d1901-ef21-4aa7-9d0a-6bbeb7fadf1c
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# &#201;diteur de transformation de script (page Script)
  Utilisez l'onglet **Script** de la boîte de dialogue **Éditeur de transformation de script** pour définir un script et les propriétés associées.  
  
 Pour en savoir plus sur le composant de script, consultez [Script Component](../../../integration-services/data-flow/transformations/script-component.md) et [Configuring the Script Component in the Script Component Editor](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md). Pour en savoir plus sur la programmation du composant de script, consultez [Extending the Data Flow with the Script Component](../../../integration-services/extending-packages-scripting/data-flow-script-component/extending-the-data-flow-with-the-script-component.md).  
  
## Options  
 **Propriétés**  
 Affichez et modifiez les propriétés de la transformation de script. La plupart des propriétés affichées sont en lecture seule. Vous pouvez modifier les propriétés suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Description**|Décrit la transformation de script en terme de fonction.|  
|**LocaleID**|Définissez les paramètres régionaux pour fournir des informations spécifiques à la région relatives au tri et à la conversion de date et d'heure.|  
|**Nom**|Entrez un nom descriptif pour le composant.|  
|**ValidateExternalMetadata**|Indiquez si la transformation de script valide les métadonnées de colonne par rapport aux sources de données externes lors de la conception. La valeur **false** diffère la validation jusqu'à l'exécution.|  
|**ReadOnlyVariables**|Tapez une liste de variables séparées par une virgule pour l'accès en lecture seule par la transformation de script.<br /><br /> Remarque : les noms des variables respectent la casse.|  
|**ReadWriteVariables**|Tapez une liste de variables séparées par une virgule pour l'accès en lecture/écriture par la transformation de script.<br /><br /> Remarque : les noms des variables respectent la casse.|  
|**ScriptLanguage**|Sélectionnez le langage de script que le composant de script doit utiliser.<br /><br /> Pour définir le langage de script par défaut pour les composants et les tâches de script, utilisez l'option **Langage de script** dans la page **Général** de la boîte de dialogue **Options** .|  
|**UserComponentTypeName**|Spécifie la classe <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponentHost> et l’assembly **Microsoft.SqlServer.TxScript** qui prennent en charge l’infrastructure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
 **Modifier le script**  
 Utilisez [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) pour créer ou modifier un script.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Sélectionner le type de composant de script](../../../integration-services/data-flow/transformations/select-script-component-type.md)   
 [Éditeur de transformation de script &#40;page Colonnes d’entrée&#41;](../../../integration-services/data-flow/transformations/script-transformation-editor-input-columns-page.md)   
 [Éditeur de transformation de script &#40;page Entrées et sorties&#41;](../../../integration-services/data-flow/transformations/script-transformation-editor-inputs-and-outputs-page.md)   
 [Éditeur de transformation de script &#40;page Gestionnaires de connexions&#41;](../../../integration-services/data-flow/transformations/script-transformation-editor-connection-managers-page.md)   
 [Exemples supplémentaires du composant Script](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
  
  