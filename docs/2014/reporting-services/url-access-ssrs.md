---
title: Accès URL (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- URL access [Reporting Services]
- links [Reporting Services], URL access
- URL access [Reporting Services], about URL access
- parameters [Reporting Services], URL access
- report servers [Reporting Services], URL access
- hyperlinks [Reporting Services]
ms.assetid: 52c3f2a3-3d6d-4fee-9c46-83f366919398
caps.latest.revision: 43
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 1e969deea2a5a2ca99af25a763adf324818ce741
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041301"
---
# <a name="url-access-ssrs"></a>Accès URL (SSRS)
  L'accès URL du serveur de rapports dans SQL Server Reporting Services (SSRS) vous permet d'envoyer des commandes à un serveur de rapports par la biais d'une demande d'URL. Par exemple, vous pouvez personnaliser le rendu d'un rapport sur un serveur de rapports en mode natif ou dans une bibliothèque SharePoint. Vous avez peut-être affiché le rapport à l'aide d'un ensemble de valeurs de paramètre de rapport, ou vous avez peut-être consulté une page spécifique digne d'intérêt dans le rapport. Vous pouvez encapsuler ces informations dans l'URL à l'aide de paramètres d'accès URL prédéfinis. Vous pouvez personnaliser davantage la façon dont le serveur de rapports traite le rapport en incorporant des paramètres pour les formats de rendu ou pour l'apparence de la visionneuse de rapports. Vous pouvez ensuite coller cette URL directement dans un courrier électronique ou une page Web pour permettre à d'autres utilisateurs d'accéder à votre rapport de la même manière dans le navigateur.  
  
 Autres actions que vous pouvez exécuter via l'accès URL :  
  
-   Envoyer des commandes à la visionneuse HTML, notamment ajuster son apparence  
  
-   Répertorier les enfants d'un dossier de catalogue  
  
-   Récupérer la définition XML d'un élément de catalogue  
  
-   Effectuer le rendu d'un instantané d'historique de rapport  
  
-   Gérer les sessions de rapport  
  
 Pour obtenir la liste complète des commandes et les paramètres disponibles via l’accès URL, consultez [référence de paramètre d’accès URL](url-access-parameter-reference.md).  
  
## <a name="url-access-concepts"></a>Concepts d'accès URL  
 Les demandes d'URL au serveur de rapports contiennent des paramètres qui sont traités par le serveur de rapports. La façon dont le serveur de rapports gère les demandes d'URL dépend des paramètres, des préfixes de paramètres et des types d'éléments qui sont inclus dans l'URL. Les URL du serveur de rapports suivent les recommandations de mise en forme des URL indiquées dans la version préliminaire de la norme conjointe du W3C (World Wide Web Consortium) et de l'IETF. [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Les fonctionnalités d’URL sont compatibles avec la plupart des navigateurs et applications Internet qui prennent en charge l’adressage URL standard.  
  
### <a name="url-access-syntax"></a>Syntaxe de l'accès URL  
 Les demandes d'URL peuvent contenir plusieurs paramètres, indiqués sans ordre précis. Les paramètres sont séparés par une esperluette (&) et les paires nom/valeur sont séparées par un signe égal (=).  
  
```  
  
rswebserviceurl  
?  
reportpath  
      [&prefix:param=value]...n]  
  
```  
  
### <a name="syntax-description"></a>Description de la syntaxe  
 *rswebserviceurl*  
 URL du service web du serveurs de rapports. Pour le mode natif, il s’agit de l’URL du service web de l’instance du serveur de rapports configurée dans le Gestionnaire de configuration de Reporting Services (consultez [Configurer des URL de serveurs de rapports &#40;Gestionnaire de configuration de SSRS&#41;](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)). Exemple :  
  
```  
http://myrshost/reportserver  
https://machine.adventure-works.com/reportserver_MYNAMEDINSTANCE  
```  
  
 Pour le mode intégré SharePoint, il s’agit de l’URL du proxy [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sur un site SharePoint intégré à [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]. Exemple :  
  
```  
http://myspsite/subsite/_vti_bin/reportserver  
```  
  
> [!TIP]  
>  Il est important que l'URL inclue la syntaxe de proxy `_vti_bin` pour acheminer la requête via SharePoint et le proxy HTTP [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] . Le proxy ajoute à la requête HTTP le contexte nécessaire pour garantir une exécution correcte du rapport pour les serveurs de rapports en mode SharePoint.  
  
 *pathinfo*  
 Chemin relatif de l’élément dans la base de données du serveur de rapports en mode natif, ou URL complète de l’élément dans un catalogue SharePoint.  
  
 Chemin de l’élément du catalogue. Pour le mode natif, il s'agit du chemin d'accès relatif de l'élément dans la base de données du serveur de rapports, commençant par une barre oblique (`/`). Exemple :  
  
```  
/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2  
```  
  
 Pour le mode intégré SharePoint, il s'agit de l'URL complète de l'élément dans la bibliothèque SharePoint, y compris l'extension d'élément. Exemple :  
  
```  
http://myspsite/subsite/AdventureWorks 2008R2/Employee_Sales_Summary_2008R2.rdl  
```  
  
 `&`  
 Utilisé pour séparer les paires nom/valeur des paramètres d'accès URL.  
  
 **prefix**  
 Facultatif. Préfixe de paramètre d’accès URL (par exemple, `rs:` ou `rc:`) qui permet d’accéder à un processus spécifique exécuté sur le serveur de rapports.  
  
> [!NOTE]  
>  Si aucun préfixe n'est spécifié pour un paramètre d'accès URL, ce dernier est traité par le serveur de rapports comme un paramètre de rapport. Les paramètres de rapport n'utilisent pas de préfixe de paramètre et respectent la casse.  
  
 **param**  
 Le nom du paramètre.  
  
 *valeur*  
 Texte d'URL correspondant à la valeur du paramètre utilisé.  
  
 **Remarque :** pour obtenir la liste des paramètres d’accès URL disponibles, consultez [référence de paramètre d’accès URL](url-access-parameter-reference.md). Pour obtenir des exemples en passant les paramètres de rapport sur l’URL, consultez [passer un paramètre de rapport dans une URL](pass-a-report-parameter-within-a-url.md).  
  
## <a name="related-tasks"></a>Related Tasks  
  
|Descriptions de tâche|Liens|  
|-----------------------|-----------|  
|Accéder aux éléments du serveur de rapports, tels que des rapports, des sources de données partagées, et des ressources.|[Accéder à des éléments de serveurs de rapports à l'aide de l'accès URL](access-report-server-items-using-url-access.md)|  
|Passer des paramètres de rapport à un rapport.|[Passer un paramètre de rapport dans une URL](pass-a-report-parameter-within-a-url.md)|  
|Définir les paramètres régionaux des paramètres de rapport dans la chaîne d'accès URL, qui définit les traductions spécifiques aux paramètres régionaux des dates, des devises, et ainsi de suite.|[Définir la langue des paramètres de rapport dans une URL](set-the-language-for-report-parameters-in-a-url.md)|  
|Envoyer les paramètres spécifiques d'extension de rendu qui personnalisent le rendu du rapport.|[Spécifier les paramètres d’informations des périphériques dans une URL](specify-device-information-settings-in-a-url.md)|  
|Exporter un rapport directement vers un format de fichier sans l'afficher dans le navigateur.|[Exporter un rapport à l’aide de l’accès URL](export-a-report-using-url-access.md)|  
|Ouvrir un rapport et accéder directement à l'emplacement d'une chaîne.|[Rechercher un rapport à l'aide de l'accès URL](search-a-report-using-url-access.md)|  
|Effectuer le rendu d'un instantané d'historique de rapport.|[Rendre un instantané d'historique de rapports à l'aide de l'accès URL](render-a-report-history-snapshot-using-url-access.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Passer un paramètre de rapport dans une URL](pass-a-report-parameter-within-a-url.md)   
 [Référence de paramètres d’accès URL](url-access-parameter-reference.md)   
 [Intégration de Reporting Services à l’aide de l’accès URL](application-integration/integrating-reporting-services-using-url-access.md)   
 [Recherche, affichage et gestion de rapports &#40;Générateur de rapports et SSRS&#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  