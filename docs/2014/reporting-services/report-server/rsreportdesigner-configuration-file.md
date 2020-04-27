---
title: Fichier de configuration RSReportDesigner | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], configuration file
- RSReportDesigner configuration file
ms.assetid: fdcc9c58-3bad-45b3-ba8e-c7816d64f14c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f5ba4168f5417260b0857accdb9cf8fb3fa0f3c0
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66103337"
---
# <a name="rsreportdesigner-configuration-file"></a>fichier de configuration RSReportDesigner
  Le fichier RSReportDesigner.config stocke les paramètres relatifs aux extensions de rendu et de traitement de données accessibles au Concepteur de rapports. Les informations d'extension pour le traitement des données sont stockées dans l'élément `Data`. Les informations d'extension de rendu sont stockées dans l'élément `Render`. L'élément `Designer` énumère les générateurs de requêtes utilisés dans le Concepteur de rapports.  
  
 Le Concepteur de rapports utilise la fonctionnalité de serveur de rapports incorporée pour afficher un aperçu des rapports. Des paramètres serveur peuvent être spécifiés pour prendre en charge le traitement local côté serveur des opérations d'aperçu. Pour plus d’informations sur les paramètres de configuration du serveur de rapports, consultez le [fichier de configuration RSReportServer](rsreportserver-config-configuration-file.md).  
  
## <a name="file-location"></a>Emplacement du fichier  
 Ce fichier se trouve à l'emplacement \Program Files\Microsoft Visual Studio 8\Common7\IDE\PrivateAssemblies.  
  
## <a name="editing-guidelines"></a>Instructions de modification  
 Ne modifiez pas les paramètres de ce fichier sauf si vous déployez ou supprimez une extension personnalisée, désactivez la mise en cache lors de l'aperçu ou inscrivez une nouvelle extension de traitement des données après la mise à niveau d'un Service Pack.  
  
 Des instructions spécifiques relatives à la modification des fichiers de configuration sont disponibles si vous personnalisez des paramètres d'extension de rendu. Pour plus d’informations, consultez [Personnaliser les paramètres d’extension de rendu dans RSReportServer.Config](../customize-rendering-extension-parameters-in-rsreportserver-config.md).  
  
 Pour obtenir des instructions sur la modification des fichiers de configuration, consultez [Modifier un fichier de configuration Reporting Services &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md).  
  
## <a name="example-configuration-file"></a>Exemple de fichier de configuration  
 L'exemple suivant illustre le format du fichier RSReportDesigner.config.  
  
```  
<Configuration>  
  <Add Key="SecureConnectionLevel" Value="0" />  
  <Add Key="InstanceName" Value="Microsoft.ReportingServices.PreviewServer" />  
  <Add Key="SessionCookies" Value="true" />  
  <Add Key="SessionTimeoutMinutes" Value="3" />  
  <Add Key="PolicyLevel" Value="rspreviewpolicy.config" />  
  <Add Key="CacheDataForPreview" Value="true" />  
  <Extensions>  
    <Render> . . . </Render>  
    <Data> . . . </Data>  
    <Designer> . . . </Designer>  
```  
  
## <a name="configuration-settings"></a>Paramètres de configuration  
  
|Paramètre|Description|  
|-------------|-----------------|  
|`SecureConnectionLevel`|Spécifie le niveau de sécurité de la connexion du service Web. La plage des valeurs valides s'étend de 0 (niveau le plus faible) à 3. Pour plus d’informations, consultez [Utilisation des méthodes de service web sécurisées](../report-server-web-service/net-framework/using-secure-web-service-methods.md).|  
|`InstanceName`|Identificateur du serveur pour l'aperçu. Ne modifiez pas cette valeur.|  
|`SessionCookies`|Spécifie si le serveur de rapports utilise des cookies de navigateur pour conserver les informations de session. Les valeurs autorisées comprennent `true` et `false`. Par défaut, il s’agit de `true`. Si vous définissez cette valeur sur « false », les données de session sont stockées dans la base de données **reportservertempdb** .|  
|`SessionTimeoutMinutes`|Spécifie la durée pendant laquelle un cookie de session est valable. La valeur par défaut est 3 minutes.|  
|`PolicyLevel`|Spécifie le fichier de configuration de la stratégie de sécurité. La valeur valide est rspreviewpolicy. config. Pour plus d’informations, consultez [utilisation des fichiers de stratégie de sécurité Reporting Services](../extensions/secure-development/using-reporting-services-security-policy-files.md).|  
|`CacheDataForPreview`|Si vous affectez la valeur `True` à ce paramètre, le Concepteur de rapports stocke les données dans un fichier mis en cache sur l'ordinateur local. Les valeurs valides sont `True` (valeur par défaut) et `False`. Pour plus d’informations, consultez [Aperçu des rapports](../reports/previewing-reports.md).|  
|`Render`|Énumère les extensions de rendu accessibles au Concepteur de rapports à des fins d'aperçu. L'ensemble des extensions de rendu utilisé pour l'aperçu doit être identique à celui installé avec le serveur de rapports.<br /><br /> `Name` spécifie l'extension de rendu. Si vous appelez une extension de rendu à l'aide de code, utilisez cette valeur pour appeler une extension spécifique.<br /><br /> `Type` spécifie le nom de classe complet de la classe d'extension et le nom de la bibliothèque séparés par une virgule.<br /><br /> `Visible` spécifie si le nom apparaît dans une interface utilisateur. Cette valeur peut être `True` (par défaut) ou `False`. Si la valeur est `True`, le nom apparaît dans les interfaces utilisateur.|  
|`Data`|Énumère les extensions de traitement des données accessibles au Concepteur de rapports pour se connecter aux sources de données qui alimentent les rapports. L'ensemble d'extensions de traitement de données utilisé dans le Concepteur de rapports peut être identique à celui installé avec le serveur de rapports. Si vous ajoutez ou que vous supprimez des extensions personnalisées, consultez [Déploiement d’une extension pour le traitement des données](../extensions/data-processing/deploying-a-data-processing-extension.md).<br /><br /> `Name` spécifie l'extension pour le traitement des données.<br /><br /> `Type` spécifie le nom de classe complet de la classe d'extension et le nom de la bibliothèque séparés par une virgule.|  
|`Designer`|Énumère les générateurs de requêtes accessibles au Concepteur de rapports. Les générateurs de requête fournissent une interface utilisateur pour générer des requêtes permettant d'extraire des données pour les rapports. Ils peuvent varier en fonction des extensions de traitement de données. Par défaut, Reporting Services fournit une interface utilisateur d'outil de données visuelle pour toutes les extensions de traitement de données qui sont incluses dans le produit. Toutefois, si vous développez ou utilisez des extensions de traitement de données tierces, d'autres interfaces de générateurs de requête peuvent être utilisées.|  
|`PreviewProcessingServiceStartupTimeoutSeconds`|Spécifie la durée d'attente pour le démarrage du service de traitement des aperçus avant l'affichage d'un message d'erreur. La valeur par défaut est 15 secondes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de configuration de Reporting Services](reporting-services-configuration-files.md)   
 [Outils de conception de requête dans Concepteur de rapports SQL Server Data Tools &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md)  
  
  
