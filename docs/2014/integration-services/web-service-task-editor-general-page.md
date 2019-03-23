---
title: Éditeur de tâche de Service Web (Page Général) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.general.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 4890f4c56e207432a5b64cd04a0bfeac15135b1b
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58374747"
---
# <a name="web-service-task-editor-general-page"></a>Éditeur de tâche de service Web (page Général)
  Utilisez la page **Général** de la boîte de dialogue **Éditeur de tâche de service Web** pour définir un gestionnaire de connexions HTTP, spécifier l’emplacement du fichier WSDL (Web Services Description Language) qu’utilise la tâche de service web, décrire la tâche de service web et télécharger le fichier WSDL.  
  
 Pour plus d’informations sur cette tâche, consultez [Tâche de service Web](control-flow/web-service-task.md).  
  
## <a name="options"></a>Options  
 **HTTPConnection**  
 Sélectionnez un gestionnaire de connexions dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour en créer un.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions HTTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
 **Rubriques connexes :**  [Gestionnaire de connexions HTTP](connection-manager/http-connection-manager.md), [HTTP Connection Manager Editor &#40;Page du serveur&#41;](../../2014/integration-services/http-connection-manager-editor-server-page.md)  
  
 **WSDLFile**  
 Tapez le chemin d’accès qualifié complet d’un fichier WSDL qui est en local sur l’ordinateur ou cliquez sur le bouton Parcourir **(...)** et recherchez ce fichier.  
  
 Si vous avez déjà téléchargé manuellement le fichier WSDL sur l'ordinateur, sélectionnez-le. Toutefois, si le fichier WSDL n'a pas encore été téléchargé, procédez comme suit :  
  
-   Créez un fichier vide ayant l'extension de nom de fichier .wsdl.  
  
-   Sélectionnez ce fichier vide pour l’option **WSDLFile** .  
  
-   Définissez la valeur de **OverwriteWSDLFile** à `True` à activer le fichier vide être remplacé par le fichier WSDL réel.  
  
-   Cliquez sur **Télécharger WSDL** pour télécharger le fichier WSDL réel et remplacer le fichier vide.  
  
    > [!NOTE]  
    >  L’option **Télécharger WSDL** n’est pas activée tant que vous n’avez pas indiqué le nom d’un fichier local existant dans la zone **WSDLFile** .  
  
 **OverwriteWSDLFile**  
 Indiquez si le fichier WSDL de la tâche de service Web peut être remplacé.  
  
 Si vous projetez de télécharger le fichier WSDL à l’aide de la **télécharger WSDL** bouton, définissez cette valeur sur `True`.  
  
 **Nom**  
 Fournissez un nom unique pour la tâche de service Web. Ce nom sert d'étiquette à l'icône de la tâche.  
  
> [!NOTE]  
>  Les noms de tâche doivent être uniques dans un package.  
  
 **Description**  
 Entrez une description de la tâche de service Web.  
  
 **Télécharger WSDL**  
 Téléchargez le fichier WSDL.  
  
 Ce bouton n’est pas activé tant que vous n’avez pas indiqué le nom d’un fichier local existant dans la zone **WSDLFile** .  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de service Web &#40;page Entrée&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [Éditeur de tâche de service Web &#40;page Output (Sortie)&#41;](../../2014/integration-services/web-service-task-editor-output-page.md)   
 [Page Expressions](expressions/expressions-page.md)  
  
  
