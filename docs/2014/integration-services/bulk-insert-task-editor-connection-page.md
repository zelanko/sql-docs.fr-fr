---
title: En bloc éditeur de tâche d’insertion (Page connexion) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.bulkinserttask.connection.f1
helpviewer_keywords:
- Bulk Insert Task Editor
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 04c81b9bd101ec66d0ec1f47fb4c48c2179635ba
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051782"
---
# <a name="bulk-insert-task-editor-connection-page"></a>Éditeur de tâche d'insertion en bloc (page Connexion)
  Utilisez la page **Connexion** de la boîte de dialogue **Éditeur de tâche d'insertion en bloc** pour définir la source et la destination de l'opération d'insertion en bloc et le format à utiliser.  
  
 Pour en savoir plus sur l’utilisation des insertions en bloc, consultez [Tâche d’insertion en bloc](control-flow/bulk-insert-task.md) et [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
## <a name="options"></a>Options  
 **Connexion**  
 Sélectionnez un gestionnaire de connexions OLE DB dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer une connexion.  
  
 **Rubriques connexes :** [Gestionnaire de connexions OLE DB](connection-manager/ole-db-connection-manager.md), [Configurer le gestionnaire de connexions OLE DB](../../2014/integration-services/configure-ole-db-connection-manager.md)  
  
 **Table de destination**  
 Tapez le nom de la table de destination ou affichez ou sélectionnez une table ou une vue dans la liste.  
  
 **Format**  
 Sélectionnez la source du format de l'insertion en bloc. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Utiliser un fichier**|Sélectionnez un fichier contenant la spécification de format. Cette option affiche l'option dynamique **FormatFile**.|  
|**Spécifier**|Spécifiez le format. Cette option affiche les options dynamiques `RowDelimiter` et `ColumnDelimiter`.|  
  
 **Fichier**  
 Sélectionnez un gestionnaire de connexions de fichiers ou de fichiers plats dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer une connexion.  
  
 L'emplacement du fichier dépend du moteur de base de données SQL Server spécifié dans le gestionnaire de connexions pour cette tâche. Le fichier texte doit être accessible au moteur de base de données SQL Server situé sur un disque dur local du serveur ou via un partage ou un lecteur mappé à SQL Server. Le fichier n'est pas accessible au runtime SSIS.  
  
 Si vous accédez au fichier source en utilisant un gestionnaire de connexions de fichiers plats, la tâche d'insertion en bloc n'utilise pas le format défini dans le gestionnaire de connexions de fichiers plats. Elle utilise à la place le format spécifié dans un fichier de format, ou les valeurs des propriétés RowDelimiter et ColumnDelimiter de la tâche.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../2014/integration-services/file-connection-manager-editor.md), [Gestionnaire de connexions de fichiers plats](connection-manager/flat-file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Général&#41;](general-page-of-integration-services-designers-options.md), [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Colonnes&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md), [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Avancé&#41;](../../2014/integration-services/flat-file-connection-manager-editor-advanced-page.md)  
  
 **Actualiser les tables**  
 Actualise la liste des tables et des vues.  
  
## <a name="format-dynamic-options"></a>Options dynamiques de format  
  
### <a name="format--use-file"></a>Format = Utiliser un fichier  
 **FormatFile**  
 Tapez le chemin du fichier de format ou cliquez sur le bouton avec des points de suspension **(…)** pour rechercher le fichier de format.  
  
### <a name="format--specify"></a>Format = Spécifier  
 `RowDelimiter`  
 Spécifiez le délimiteur de ligne dans le fichier source. La valeur par défaut est **{CR}{LF}**.  
  
 `ColumnDelimiter`  
 Spécifiez le délimiteur de colonne dans le fichier source. La valeur par défaut est **Tab**.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche d’insertion en bloc de &#40;Page Général&#41;](../../2014/integration-services/bulk-insert-task-editor-general-page.md)   
 [Éditeur de tâche d’insertion en bloc de &#40;Page Options&#41;](../../2014/integration-services/bulk-insert-task-editor-options-page.md)   
 [Page expressions](expressions/expressions-page.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)   
 [Flux de contrôle](control-flow/control-flow.md)  
  
  
