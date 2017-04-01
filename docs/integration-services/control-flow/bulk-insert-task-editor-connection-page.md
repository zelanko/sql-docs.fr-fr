---
title: "&#201;diteur de t&#226;che d&#39;insertion en bloc (page Connexion) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.bulkinserttask.connection.f1"
helpviewer_keywords: 
  - "Éditeur de tâche d'insertion en bloc"
ms.assetid: 51252c20-8865-4ede-a3fd-bd73a968f47d
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# &#201;diteur de t&#226;che d&#39;insertion en bloc (page Connexion)
  Utilisez la page **Connexion** de la boîte de dialogue **Éditeur de tâche d'insertion en bloc** pour définir la source et la destination de l'opération d'insertion en bloc et le format à utiliser.  
  
 Pour en savoir plus sur l’utilisation des insertions en bloc, consultez [Tâche d’insertion en bloc](../../integration-services/control-flow/bulk-insert-task.md) et [Fichiers de format pour l’importation ou l’exportation de données &#40;SQL Server&#41;](../../relational-databases/import-export/format-files-for-importing-or-exporting-data-sql-server.md).  
  
## Options  
 **Connexion**  
 Sélectionnez un gestionnaire de connexions OLE DB dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer une connexion.  
  
 **Rubriques connexes :** [Gestionnaire de connexions OLE DB](../../integration-services/connection-manager/ole-db-connection-manager.md), [Configurer le gestionnaire de connexions OLE DB](../../integration-services/connection-manager/configure-ole-db-connection-manager.md)  
  
 **Table de destination**  
 Tapez le nom de la table de destination ou affichez ou sélectionnez une table ou une vue dans la liste.  
  
 **Format**  
 Sélectionnez la source du format de l'insertion en bloc. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Utiliser un fichier**|Sélectionnez un fichier contenant la spécification de format. Cette option affiche l'option dynamique **FormatFile**.|  
|**Spécifier**|Spécifiez le format. Cette option affiche les options dynamiques **RowDelimiter** et **ColumnDelimiter**.|  
  
 **Fichier**  
 Sélectionnez un gestionnaire de connexions de fichiers ou de fichiers plats dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer une connexion.  
  
 L'emplacement du fichier dépend du moteur de base de données SQL Server spécifié dans le gestionnaire de connexions pour cette tâche. Le fichier texte doit être accessible au moteur de base de données SQL Server situé sur un disque dur local du serveur ou via un partage ou un lecteur mappé à SQL Server. Le fichier n'est pas accessible au runtime SSIS.  
  
 Si vous accédez au fichier source en utilisant un gestionnaire de connexions de fichiers plats, la tâche d'insertion en bloc n'utilise pas le format défini dans le gestionnaire de connexions de fichiers plats. Elle utilise à la place le format spécifié dans un fichier de format, ou les valeurs des propriétés RowDelimiter et ColumnDelimiter de la tâche.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers](../../integration-services/connection-manager/file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers](../../integration-services/connection-manager/file-connection-manager-editor.md), [Gestionnaire de connexions de fichiers plats](../../integration-services/connection-manager/flat-file-connection-manager.md), [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Général&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-general-page.md), [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Colonnes&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-columns-page.md), [Éditeur du gestionnaire de connexions de fichiers plats &#40;page Avancé&#41;](../../integration-services/connection-manager/flat-file-connection-manager-editor-advanced-page.md)  
  
 **Actualiser les tables**  
 Actualise la liste des tables et des vues.  
  
## Options dynamiques de format  
  
### Format = Utiliser un fichier  
 **FormatFile**  
 Tapez le chemin du fichier de format ou cliquez sur le bouton avec des points de suspension **(…)** pour rechercher le fichier de format.  
  
### Format = Spécifier  
 **RowDelimiter**  
 Spécifiez le délimiteur de ligne dans le fichier source. La valeur par défaut est **{CR}{LF}**.  
  
 **ColumnDelimiter**  
 Spécifiez le délimiteur de colonne dans le fichier source. La valeur par défaut est **Tab**.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche d’insertion en bloc &#40;page Général&#41;](../../integration-services/control-flow/bulk-insert-task-editor-general-page.md)   
 [Éditeur de tâche d’insertion en bloc &#40;page Options&#41;](../../integration-services/control-flow/bulk-insert-task-editor-options-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [Flux de contrôle](../../integration-services/control-flow/control-flow.md)  
  
  