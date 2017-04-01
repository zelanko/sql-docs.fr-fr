---
title: "&#201;diteur de t&#226;che de service Web (page G&#233;n&#233;ral) | Microsoft Docs"
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
  - "sql13.dts.designer.webservicestask.general.f1"
helpviewer_keywords: 
  - "Éditeur de tâche de service Web"
ms.assetid: 4d7df283-430d-4f0f-9dd4-5909554cd5eb
caps.latest.revision: 34
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 34
---
# &#201;diteur de t&#226;che de service Web (page G&#233;n&#233;ral)
  Utilisez la page **Général** de la boîte de dialogue **Éditeur de tâche de service Web** pour définir un gestionnaire de connexions HTTP, spécifier l’emplacement du fichier WSDL (Web Services Description Language) qu’utilise la tâche de service web, décrire la tâche de service web et télécharger le fichier WSDL.  
  
 Pour plus d’informations sur cette tâche, consultez [Tâche de service Web](../../integration-services/control-flow/web-service-task.md).  
  
## Options  
 **HTTPConnection**  
 Sélectionnez un gestionnaire de connexions dans la liste ou cliquez sur \<**Nouvelle connexion...**> pour créer un gestionnaire de connexions.  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions HTTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
 **Rubriques connexes :**  [Gestionnaire de connexions HTTP](../../integration-services/connection-manager/http-connection-manager.md), [Éditeur du gestionnaire de connexions HTTP &#40;page Server (Serveur)&#41;](../../integration-services/connection-manager/http-connection-manager-editor-server-page.md)  
  
 **WSDLFile**  
 Tapez le chemin d’accès qualifié complet d’un fichier WSDL qui est en local sur l’ordinateur ou cliquez sur le bouton Parcourir **(…)** et recherchez ce fichier.  
  
 Si vous avez déjà téléchargé manuellement le fichier WSDL sur l'ordinateur, sélectionnez-le. Toutefois, si le fichier WSDL n'a pas encore été téléchargé, procédez comme suit :  
  
-   Créez un fichier vide ayant l'extension de nom de fichier .wsdl.  
  
-   Sélectionnez ce fichier vide pour l’option **WSDLFile**.  
  
-   Affectez à **OverwriteWSDLFile** la valeur **True** pour permettre le remplacement du fichier vide par le fichier WSDL réel.  
  
-   Cliquez sur **Télécharger WSDL** pour télécharger le fichier WSDL réel et remplacer le fichier vide.  
  
    > [!NOTE]  
    >  L’option **Télécharger WSDL** n’est pas activée tant que vous n’avez pas indiqué le nom d’un fichier local existant dans la zone **WSDLFile**.  
  
 **OverwriteWSDLFile**  
 Indiquez si le fichier WSDL de la tâche de service Web peut être remplacé.  
  
 Si vous projetez de télécharger le fichier WSDL à l’aide du bouton **Télécharger WSDL**, définissez cette valeur sur **True**.  
  
 **Nom**  
 Fournissez un nom unique pour la tâche de service Web. Ce nom sert d'étiquette à l'icône de la tâche.  
  
> [!NOTE]  
>  Les noms de tâche doivent être uniques dans un package.  
  
 **Description**  
 Entrez une description de la tâche de service Web.  
  
 **Télécharger WSDL**  
 Téléchargez le fichier WSDL.  
  
 Ce bouton n’est pas activé tant que vous n’avez pas indiqué le nom d’un fichier local existant dans la zone **WSDLFile**.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../integration-services/integration-services-error-and-message-reference.md)   
 [Éditeur de tâche de service Web &#40;page Entrée&#41;](../../integration-services/control-flow/web-service-task-editor-input-page.md)   
 [Éditeur de tâche de service Web &#40;page Output (Sortie)&#41;](../../integration-services/control-flow/web-service-task-editor-output-page.md)   
 [Page Expressions](../../integration-services/expressions/expressions-page.md)  
  
  