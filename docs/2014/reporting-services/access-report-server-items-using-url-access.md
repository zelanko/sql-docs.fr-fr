---
title: Accéder aux éléments de serveur de rapports à l’aide de l’accès URL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- referencing URL items for report server access
- URL access [Reporting Services], report servers
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3a345cd609c4cfd79f9e93a2b63e71bbddde36ee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63233566"
---
# <a name="access-report-server-items-using-url-access"></a>Accéder aux éléments de serveur de rapports à l’aide de l’accès URL
  Cette rubrique décrit comment accéder aux éléments du catalogue de types différents dans un rapport de données du serveur de base ou dans un site SharePoint à l’aide de *rs : Command*=*valeur*.  
  
 Il n’est pas nécessaire d’ajouter cette chaîne de paramètres. Si vous l’omettez, le serveur de rapports évalue le type d’élément et sélectionne automatiquement de la valeur du paramètre approprié. Toutefois, à l’aide de la *rs : Command*=*valeur* chaîne dans l’URL améliore les performances du serveur de rapports.  
  
 Remarque la `_vti_bin` syntaxe de proxy dans les exemples ci-dessous. Pour plus d’informations sur l’utilisation de la syntaxe de proxy, consultez [référence de paramètre d’accès URL](url-access-parameter-reference.md).  
  
## <a name="access-a-report"></a>Accéder à un rapport  
 Pour afficher un rapport dans le navigateur, utilisez le *rs : Command*=*restituer* paramètre. Exemple :  
  
 `Native` `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  Il est important que l’URL inclue la `_vti_bin` syntaxe de proxy pour acheminer la requête via SharePoint et le [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] proxy HTTP. Le proxy ajoute à la requête HTTP, le contexte qui est nécessaire pour garantir une exécution correcte du rapport pour les serveurs de rapports en mode SharePoint.  
  
## <a name="access-a-resource"></a>Accéder à une ressource  
 Pour accéder à une ressource, utilisez le *rs : Command*=*GetResourceContents* paramètre. Si la ressource est compatible avec le navigateur, tel qu’une image, il est ouvert dans le navigateur. Sinon, vous êtes invité à ouvrir ou enregistrer le fichier ou la ressource sur le disque.  
  
 `Native` `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  
  
## <a name="access-a-data-source"></a>Accéder à une Source de données  
 Pour accéder à une source de données, utilisez le *rs : Command*=*GetDataSourceContents* paramètre. Si votre navigateur prend en charge XML, la définition de source de données s’affiche si vous êtes un utilisateur authentifié avec `Read Contents` autorisation sur la source de données. Exemple :  
  
 `Native` `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 La structure XML peut ressembler à l’exemple suivant :  
  
```  
<DataSourceDefinition>  
   <Extension>SQL</Extension>  
   <ConnectString>Provider=SQLOLEDB.1;Integrated Security=SSPI;Persist Security Info=False;Initial Catalog=AdventureWorks2012;Data Source=MYSERVER1;</ConnectString>  
   <CredentialRetrieval>Integrated</CredentialRetrieval>  
   <WindowsCredentials>False</WindowsCredentials>  
   <ImpersonateUser>False</ImpersonateUser>  
   <Prompt />  
   <Enabled>True</Enabled>  
</DataSourceDefinition>  
```  
  
 La chaîne de connexion est retournée selon le **SecureConnectionLevel** configuration du serveur de rapports. Pour plus d’informations sur la **SecureConnectionLevel** définition, consultez [à l’aide des méthodes de Service Web sécurisées](report-server-web-service/net-framework/using-secure-web-service-methods.md).  
  
## <a name="access-the-contents-of-a-folder"></a>Accéder au contenu d’un dossier  
 Pour accéder au contenu d’un dossier, utilisez le *rs : Command*=*GetChildren* paramètre. Une page générique de navigation de dossier est retournée qui contient des liens vers les sous-dossiers, rapports, sources de données et des ressources dans le dossier demandé. Exemple :  
  
 `Native` `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`  
  
 `SharePoint` `http://myspsite/subsite/_vti_bin/reportserver? http://myspsite/subsite/Sales&rs:Command=GetChildren`  
  
 L’interface utilisateur que vous voyez est similaire à utilisé par le mode d’exploration de répertoires [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS). Le numéro de version, y compris le numéro de build du serveur de rapports est aussi affiché sous la liste des dossiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Accès URL &#40;SSRS&#41;](url-access-ssrs.md)   
 [Référence de paramètre d’accès URL](url-access-parameter-reference.md)  
  
  
