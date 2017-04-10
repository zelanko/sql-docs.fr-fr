---
title: "Acc&#233;der &#224; des &#233;l&#233;ments de serveur de rapports &#224; l&#39;aide de l&#39;acc&#232;s URL | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "référencement d'éléments URL pour l'accès au serveur de rapports"
  - "accès URL [Reporting Services], serveurs de rapports"
ms.assetid: a58b4ca6-129d-45e9-95c7-e9169fe5bba4
caps.latest.revision: 40
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 40
---
# Acc&#233;der &#224; des &#233;l&#233;ments de serveur de rapports &#224; l&#39;aide de l&#39;acc&#232;s URL
  Cette rubrique explique comment accéder aux éléments du catalogue de types différents dans une base de données du serveur de rapports ou dans un site SharePoint en utilisant *rs:Command*=*Valeur*. Il n'est pas nécessaire d'ajouter cette chaîne de paramètres. Si vous l'omettez, le serveur de rapports évalue le type d'élément et sélectionne automatiquement la valeur du paramètre appropriée. Toutefois, l’utilisation de la chaîne *rs:Command*=*Valeur* dans l’URL améliore les performances du serveur de rapports.  
  
 Notez la syntaxe de proxy `_vti_bin` dans les exemples ci-dessous. Pour plus d’informations sur l’utilisation de la syntaxe de proxy, consultez [Informations de référence sur les paramètres d’accès URL](../reporting-services/url-access-parameter-reference.md).  
  
## Accéder à un rapport  
 Pour afficher un rapport dans le navigateur, utilisez le paramètre *rs:Command*=*Render*. Par exemple :  
  
 **Natif** `http://myrshost/reportserver?/Sales/YearlySalesByCategory&rs:Command=Render`  
  
 **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/YearlySalesByCategory&rs:Command=Render`  
  
> [!TIP]  
>  Il est important que l'URL inclue la syntaxe de proxy `_vti_bin` pour acheminer la requête via SharePoint et le proxy HTTP [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Le proxy ajoute à la requête HTTP le contexte nécessaire pour garantir une exécution correcte du rapport pour les serveurs de rapports en mode SharePoint.  
  
## Accéder à une ressource  
 Pour accéder à une ressource, utilisez le paramètre *rs:Command*=*GetResourceContents*. Si la ressource est compatible avec le navigateur (une image par exemple), elle est ouverte dans le navigateur. Sinon, vous êtes invité à ouvrir ou enregistrer le fichier ou la ressource sur le disque.  
  
 **Natif** `http://myrshost/reportserver?/Sales/StorePicture&rs:Command=GetResourceContents`  
  
 **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/StorePicture.jpg&rs:Command=GetResourceContents`  
  
## Accéder à une source de données  
 Pour accéder à une source de données, utilisez le paramètre *rs:Command*=*GetDataSourceContents*. Si votre navigateur prend en charge XML, la définition de la source de données est affichée si vous êtes un utilisateur authentifié avec l’autorisation **Read Contents** sur la source des données. Par exemple :  
  
 **Natif** `http://myrshost/reportserver?/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales/AdventureWorks2012&rs:Command=GetDataSourceContents`  
  
 La structure XML peut ressembler à l'exemple suivant :  
  
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
  
 La chaîne de connexion est retournée selon le paramètre **SecureConnectionLevel** du serveur de rapports. Pour plus d’informations sur le paramètre **SecureConnectionLevel**, consultez [Utilisation des méthodes de service web sécurisées](../reporting-services/report-server-web-service/net-framework/using-secure-web-service-methods.md).  
  
## Accéder au contenu d'un dossier  
 Pour accéder au contenu d’un dossier, utilisez le paramètre *rs:Command*=*GetChildren*. Il retourne une page générique de navigation des dossiers qui contient des liens vers les sous-dossiers, rapports, sources de données et ressources dans le dossier demandé. Par exemple :  
  
 **Natif** `http://myrshost/reportserver?/Sales&rs:Command=GetChildren`  
  
 **SharePoint** `http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/Sales&rs:Command=GetChildren`  
  
 L'interface utilisateur qui s'affiche est similaire au mode d'exploration de répertoires utilisé par [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Information Server (IIS). Le numéro de version, y compris le numéro de build spécifique, du serveur de rapports est aussi affiché sous la liste des dossiers.  
  
## Voir aussi  
 [Accès URL &#40;SSRS&#41;](../reporting-services/url-access-ssrs.md)   
 [Référence de paramètre d'accès URL](../reporting-services/url-access-parameter-reference.md)  
  
  