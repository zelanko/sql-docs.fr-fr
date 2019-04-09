---
title: Source CDC | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.designer.cdcsource.f1
ms.assetid: 99775608-e177-44ed-bb44-aaccb0f4f327
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4572e9fc61649f638b7c86ee23c75450216a4342
ms.sourcegitcommit: aa4f594ec6d3e85d0a1da6e69fa0c2070d42e1d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59241787"
---
# <a name="cdc-source"></a>Source CDC
  La source CDC lit une plage de données modifiées dans les tables de modifications de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et apporte les modifications en aval aux autres composants SSIS.  
  
 La plage de données modifiées lue par la source CDC est appelée « plage de traitement de capture de données modifiées » et est déterminée par la tâche de contrôle de capture de données modifiées exécutée avant le démarrage du flux de données actuel. La plage de traitement de capture de données modifiées est dérivée de la valeur d'une variable de package qui gère l'état du traitement de capture de données modifiées pour un groupe de tables.  
  
 La source CDC extrait les données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’une table de base de données, d’une vue ou d’une instruction SQL.  
  
 La source CDC utilise les configurations suivantes :  
  
-   Un gestionnaire de connexions ADO.NET [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accéder à la base de données CDC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations sur la configuration de la connexion à la source CDC, consultez [CDC Source Editor &#40;Connection Manager Page&#41;](../cdc-source-editor-connection-manager-page.md).  
  
-   Une table pour laquelle la capture de données modifiées est activée.  
  
-   Le nom de l'instance de capture de la table sélectionnée (s'il en existe plusieurs).  
  
-   Le mode de traitement des modifications.  
  
-   Le nom de la variable de package d'état de capture de données modifiées à partir de laquelle la plage de traitement de capture de données modifiées est déterminée. La source CDC ne modifie pas cette variable.  
  
 Les données retournées par la source CDC sont les mêmes que celles retournées par les fonctions CDC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **cdc.fn_cdc_get_all_changes_\<nom-instance-capture>** ou **cdc.fn_cdc_get_net_changes_\<nom-instance-capture>** (si disponibles). Le seul ajout facultatif est la colonne **__$initial_processing** qui indique si la plage de traitement actuelle peut chevaucher une charge initiale de la table. Pour plus d’informations sur la traitement initial, consultez [Tâche de contrôle de capture de données modifiées](../control-flow/cdc-control-task.md).  
  
 La source CDC a une sortie normale et une sortie d'erreur.  
  
## <a name="error-handling"></a>Gestion des erreurs  
 la source CDC a une sortie d'erreur. La sortie d'erreur du composant contient les colonnes de sortie suivantes :  
  
-   **Code d'erreur** : La valeur est toujours -1.  
  
-   **Colonne d’erreur** : colonne source à l’origine de l’erreur (pour les erreurs de conversion).  
  
-   **Colonnes de ligne d’erreur** : Données d’enregistrement à l’origine de l’erreur.  
  
 Selon le comportement paramétré pour les erreurs, la source CDC prend en charge les erreurs de retour (conversion de données, troncation) qui se produisent pendant le processus d'extraction dans la sortie d'erreur. Pour plus d’informations, consultez [CDC Source Editor &#40;Error Output Page&#41;](../cdc-source-editor-error-output-page.md).  
  
## <a name="data-type-support"></a>Prise en charge du type de données  
 Le composant source CDC pour Microsoft prend en charge tous les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont mappés à des types de données SSIS appropriés.  
  
## <a name="troubleshooting-the-cdc-source"></a>Résolution des problèmes liés à la source CDC  
 Les éléments suivants contiennent des informations utiles à la résolution des problèmes liés à la source CDC.  
  
### <a name="use-this-script-to-isolate-problems-and-reproduce-them-in-sql-server-management-studio"></a>Utilisez ce script pour isoler les problèmes et les reproduire dans SQL Server Management Studio  
 L'opération de la source CDC est régie par l'opération de la tâche de contrôle de capture de données modifiées exécutée avant d'appeler la source CDC. La tâche de contrôle de capture de données modifiées prépare la valeur de la variable de package d'état de capture de données modifiées de sorte qu'elle contienne le NSE de début et le NSE de fin. Elle exécute une fonction équivalente au script suivant :  
  
```  
use <cdc-enabled-database-name>  
               declare @start_lsn binary(10), @end_lsn binary(10)  
               set @start_lsn = sys.fn_cdc_increment_lsn(  
                       convert(binary(10),'0x' + '<value-from-state-cs>', 1))  
               set @end_lsn =   
                       convert(binary(10),'0x' + '<value-from-state-ce>', 1)  
               select * from cdc.fn_cdc_get_net_changes_dbo_Table1(@start_lsn,  
@end_lsn, '<mode>')  
```  
  
 où :  
  
-   \<cdc-enabled-database-name> est le nom de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant les tables de modifications.  
  
-   \<value-from-state-cs> est la valeur affichée dans la variable d’état de capture de données modifiées sous la forme CS/\<value-from-state-cs>/ (CS correspond à Current-processing-range-Start, début de la plage de traitement actuelle).  
  
-   \<value-from-state-ce> est la valeur affichée dans la variable d’état de capture de données modifiées sous la forme CE/\<value-from-state-cs>/ (CE correspond à Current-processing-range-End, fin de la plage de traitement actuelle).  
  
-   \<mode> correspond aux modes de traitement de capture de données modifiées. Les modes de traitement ont l’une des valeurs suivantes : **Tout**, **Tout avec les anciennes valeurs**, **NET**, **Net avec masque de mise à jour**et **Net avec fusion**.  
  
 Ce script aide à isoler les problèmes en les reproduisant dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], où il est facile de reproduire et d'identifier des erreurs.  
  
#### <a name="sql-server-error-message"></a>Message d'erreur SQL Server  
 Le message suivant peut être retourné par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
 **Un nombre insuffisant d’arguments fourni pour la procédure ou la fonction cdc.fn_cdc_get_net_changes_\<... >.**  
  
 Cette erreur n'indique pas qu'un argument est manquant. Elle signifie que les valeurs du NSE de début ou du NSE de fin dans la variable d'état de capture de données modifiées ne sont pas valides.  
  
## <a name="configuring-the-cdc-source"></a>Configuration de la source CDC  
 Vous pouvez configurer la source CDC par programme ou par le biais du concepteur SSIS.  
  
 Pour plus d’informations, consultez l’une des rubriques suivantes :  
  
-   [Éditeur de source CDC &#40;page Gestionnaire de connexions&#41;](../cdc-source-editor-connection-manager-page.md)  
  
-   [Éditeur de source CDC &#40;page Colonnes&#41;](../cdc-source-editor-columns-page.md)  
  
-   [Éditeur de source CDC &#40;page Sortie d’erreur&#41;](../cdc-source-editor-error-output-page.md)  
  
 La boîte de dialogue **Éditeur avancé** contient les propriétés qui peuvent être définies par programme.  
  
 Pour ouvrir la boîte de dialogue **Éditeur avancé** :  
  
-   Dans l’écran **Flux de données** de votre projet [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , cliquez avec le bouton droit sur la source CDC, puis sélectionnez **Afficher l’éditeur avancé**.  
  
 Pour plus d’informations sur les propriétés que vous pouvez définir dans la boîte de dialogue **Éditeur avancé** , consultez [Propriétés personnalisées des sources CDC](cdc-source-custom-properties.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Éditeur de source CDC &#40;page Gestionnaire de connexions&#41;](../cdc-source-editor-connection-manager-page.md)  
  
-   [Éditeur de source CDC &#40;page Colonnes&#41;](../cdc-source-editor-columns-page.md)  
  
-   [Éditeur de source CDC &#40;page Sortie d’erreur&#41;](../cdc-source-editor-error-output-page.md)  
  
-   [Propriétés personnalisées des sources CDC](cdc-source-custom-properties.md)  
  
-   [Extraire des données modifiées à l'aide de la source de capture de données modifiées](cdc-source.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   Entrée de blog, [Processing Modes for the CDC Source](https://www.mattmasson.com/2012/01/processing-modes-for-the-cdc-source/) (Modes de traitement pour la source CDC), sur mattmasson.com.  
  
  
