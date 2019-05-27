---
title: Éditeur de tâche FTP (Page transfert de fichiers) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.filetransfer.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 9386070902022e29ba191f24eb8fbfb10ed92b9a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66058437"
---
# <a name="ftp-task-editor-file-transfer-page"></a>Éditeur de tâche FTP (page Transfert de fichiers)
  Utilisez la page **Transfert de fichiers** de l' **Éditeur de tâche FTP** pour configurer l'opération FTP qu'exécute la tâche.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche FTP](control-flow/ftp-task.md).  
  
## <a name="options"></a>Options  
 **IsRemotePathVariable**  
 Indique si le chemin distant est stocké dans une variable. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Le chemin d'accès de destination est stocké dans une variable. Cette valeur affiche l'option dynamique **RemoteVariable**.|  
|**False**|Le chemin d'accès de destination est défini dans un gestionnaire de connexions de fichiers. Cette valeur affiche l'option dynamique **RemovePath**.|  
  
 **OverwriteFileAtDestination**  
 Indique si un fichier peut être remplacé dans la destination.  
  
 **IsLocalPathVariable**  
 Indique si le chemin local est stocké dans une variable. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**True**|Le chemin d'accès de destination est stocké dans une variable. Cette valeur affiche l'option dynamique **LocalVariable**.|  
|**False**|Le chemin d'accès de destination est défini dans un gestionnaire de connexions de fichiers. Cette valeur affiche l'option dynamique **LocalPath**.|  
  
 **Opération**  
 Sélectionnez l'opération FTP à exécuter. Cette propriété dispose des options répertoriées dans le tableau suivant.  
  
|Value|Description|  
|-----------|-----------------|  
|**Envoyer des fichiers**|Envoie des fichiers. Cette valeur affiche les options dynamiques **LocalVariable**, **LocalPathRemoteVariable** et **RemotePath**.|  
|**Recevoir des fichiers**|Reçoit des fichiers. Cette valeur affiche les options dynamiques **LocalVariable**, **LocalPathRemoteVariable** et **RemotePath**.|  
|**Créer un répertoire local**|Crée un répertoire local. Cette valeur affiche les options dynamiques **LocalVariable** et **LocalPath**.|  
|**Créer un répertoire distant**|Crée un répertoire distant. Cette valeur affiche les options dynamiques **RemoteVariable** et **RemotePath**.|  
|**Supprimer le répertoire local**|Supprime un répertoire local. Cette valeur affiche les options dynamiques **LocalVariable** et **LocalPath**.|  
|**Supprimer le répertoire distant**|Supprime un répertoire distant. Cette valeur affiche les options dynamiques **RemoteVariable** et **RemotePath**.|  
|**Supprimer des fichiers locaux**|Supprime des fichiers locaux Cette valeur affiche les options dynamiques **LocalVariable** et **LocalPath**.|  
|**Supprimer des fichiers distants**|Supprime des fichiers distants. Cette valeur affiche les options dynamiques **RemoteVariable** et **RemotePath**.|  
  
 **IsTransferASCII**  
 Indique si les fichiers transférés vers et depuis le serveur FTP distant doivent être transférés en mode ASCII.  
  
## <a name="isremotepathvariable-dynamic-options"></a>Options dynamiques IsRemotePathVariable  
  
### <a name="isremotepathvariable--true"></a>IsRemotePathVariable = True  
 **RemoteVariable**  
 Sélectionnez une variable définie par l’utilisateur existante ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), Ajouter une variable  
  
### <a name="isremotepathvariable--false"></a>IsRemotePathVariable = False  
 **RemovePath**  
 Sélectionnez un gestionnaire de connexions FTP existant ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaires de connexions FTP](connection-manager/ftp-connection-manager.md), [Éditeur du gestionnaire de connexions FTP](../../2014/integration-services/ftp-connection-manager-editor.md)  
  
## <a name="islocalpathvariable-dynamic-options"></a>Options dynamiques IsLocalPathVariable  
  
### <a name="islocalpathvariable--true"></a>IsLocalPathVariable = True  
 **LocalVariable**  
 Sélectionnez une variable définie par l’utilisateur existante ou cliquez sur \<**Nouvelle variable...**> pour en créer une.  
  
 **Rubriques connexes :** [Variables Integration Services &#40;SSIS&#41;](integration-services-ssis-variables.md), Ajouter une variable  
  
### <a name="islocalpathvariable--false"></a>IsLocalPathVariable = False  
 **LocalPath**  
 Sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
 **Rubriques connexes :** [Gestionnaire de connexions de fichiers plats](connection-manager/file-connection-manager.md), [File Connection Manager Editor](../../2014/integration-services/file-connection-manager-editor.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche FTP &#40;page Général&#41;](general-page-of-integration-services-designers-options.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
