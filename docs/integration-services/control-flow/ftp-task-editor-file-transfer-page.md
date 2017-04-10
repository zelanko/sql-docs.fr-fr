---
title: "&#201;diteur de t&#226;che FTP (page Transfert de fichiers) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.ftptask.filetransfer.f1"
helpviewer_keywords: 
  - "Éditeur de tâche FTP"
ms.assetid: 37e52220-feb2-474c-ad88-fa1b1059acd4
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# &#201;diteur de t&#226;che FTP (page Transfert de fichiers)
  Utilisez la page **Transfert de fichiers** de l' **Éditeur de tâche FTP** pour configurer l'opération FTP qu'exécute la tâche.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche FTP](../../integration-services/control-flow/ftp-task.md).  
  
## Options  
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
  
## Options dynamiques IsRemotePathVariable  
  
### IsRemotePathVariable = True  
 **RemoteVariable**  
 Sélectionnez une variable définie par l’utilisateur existante ou cliquez sur \<**Nouvelle variable...**> pour créer une variable définie par l’utilisateur.  
  
 **Rubriques connexes :** [Integration Services &#40;SSIS&#41; Variables](../../integration-services/integration-services-ssis-variables.md), Ajouter une variable  
  
### IsRemotePathVariable = False  
 **RemotePath**  
 Sélectionnez un gestionnaire de connexions FTP existant ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [Gestionnaires de connexion FTP](../../integration-services/connection-manager/ftp-connection-manager.md), [Éditeur du gestionnaire de connexions FTP](../../integration-services/connection-manager/ftp-connection-manager-editor.md)  
  
## Options dynamiques IsLocalPathVariable  
  
### IsLocalPathVariable = True  
 **LocalVariable**  
 Sélectionnez une variable définie par l’utilisateur existante ou cliquez sur \<**Nouvelle variable...**> pour créer une variable.  
  
 **Rubriques connexes :** [Integration Services &#40;SSIS&#41; Variables](../../integration-services/integration-services-ssis-variables.md), Ajouter une variable  
  
### IsLocalPathVariable = False  
 **LocalPath**  
 Sélectionnez un gestionnaire de connexions de fichiers existant ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
 **Rubriques connexes :** [Flat File Connection Manager](../../integration-services/connection-manager/flat-file-connection-manager.md), [File Connection Manager Editor](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche FTP &#40;page Général&#41;](../../integration-services/control-flow/ftp-task-editor-general-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
  