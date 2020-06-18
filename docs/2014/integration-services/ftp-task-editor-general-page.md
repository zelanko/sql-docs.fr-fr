---
title: Éditeur de tâche FTP (page général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.general.f1
helpviewer_keywords:
- File Transfer Protocol Task Editor
ms.assetid: 28b46fdd-b04a-4f97-a99f-883f5735a6d9
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 02ffd6309ae31f538fecdf6af2cb8475608d6cf5
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966336"
---
# <a name="ftp-task-editor-general-page"></a>Éditeur de tâche FTP (page Général)
  La page **Général** de la boîte de dialogue **Éditeur de tâche FTP** permet de spécifier le gestionnaire de connexions FTP qui se connecte au serveur FTP avec lequel la tâche communique. Vous pouvez également nommer et décrire cette tâche FTP.  
  
 Pour en savoir plus sur cette tâche, consultez [Tâche FTP](control-flow/ftp-task.md).  
  
## <a name="options"></a>Options  
 **Connexion FTP**  
 Sélectionnez un gestionnaire de connexions FTP existant ou cliquez sur \<**New connection...**> pour créer un gestionnaire de connexions.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions FTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
 **Rubriques connexes :**[Gestionnaires de connexion FTP](connection-manager/ftp-connection-manager.md), [Éditeur du gestionnaire de connexions FTP](../../2014/integration-services/ftp-connection-manager-editor.md)  
  
 **Arrêt en cas d'échec de l'opération**  
 Indique si la tâche FTP se termine en cas d'échec de l'opération.  
  
 **Nom**  
 Fournit un nom unique pour la tâche FTP. Ce nom sert d'étiquette à l'icône de la tâche.  
  
> [!NOTE]  
>  Les noms de tâche doivent être uniques dans un package.  
  
 **Description**  
 Tapez une description de la tâche FTP.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services de référence des erreurs et des messages](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche FTP &#40;page transfert de fichiers&#41;](../../2014/integration-services/ftp-task-editor-file-transfer-page.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
