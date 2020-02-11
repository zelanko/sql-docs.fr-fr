---
title: Sécurité d’accès du code dans Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- code access security [Reporting Services]
- permission sets [Reporting Services]
- evidence [Reporting Services]
- code access security [Reporting Services], about code access security
- named permission sets [Reporting Services]
ms.assetid: 97480368-1fc3-4c32-b1b0-63edfb54e472
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3dd8d60c975efa1e0a230a08cc6b1ab1a9ce149b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62985739"
---
# <a name="code-access-security-in-reporting-services"></a>Sécurité d'accès du code dans Reporting Services
  La sécurité d'accès du code est axée sur les concepts principaux suivants : preuve, groupes de codes et jeux d'autorisations nommés. Dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], les composants du Gestionnaire de rapports, du Concepteur de rapports et de Report Server ont chacun un fichier de stratégie qui configure la sécurité d'accès du code pour les assemblys personnalisés, ainsi que pour les extensions de remise des données, de rendu et de sécurité. Les sections suivantes fournissent une vue d'ensemble de la sécurité d'accès du code. Pour plus d’informations sur les rubriques traitées dans cette section, consultez « modèle de stratégie de sécurité » [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] dans la documentation du kit de développement logiciel (SDK).  
  
 
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] utilise la sécurité d'accès du code, car bien que le serveur de rapports repose sur la technologie [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], il existe une différence considérable entre une application [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] classique et le serveur de rapports. Une application [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] classique n'exécute pas de code utilisateur. En revanche, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] se sert d’une architecture ouverte et extensible qui permet aux utilisateurs de programmer des fichiers de définitions de rapports à l’aide de l’élément **Code** du langage RDL (Report Definition Language), et de développer des fonctionnalités spécialisées dans un assembly personnalisé à utiliser dans les rapports. En outre, les développeurs peuvent concevoir et déployer de puissantes extensions visant à améliorer les fonctionnalités du serveur de rapports. Cette puissance et cette souplesse doivent être complétées par un niveau de protection et de sécurité optimal.  
  
 Les développeurs [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] peuvent utiliser n'importe quel assembly du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] dans leurs rapports et faire appel en mode natif à toutes les fonctionnalités des assemblys déployés dans le Global Assembly Cache. La seule chose que le serveur de rapports peut contrôler est l'autorisation accordée aux expressions de rapport et aux assemblys personnalisés chargés. Dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], les assemblys personnalisés reçoivent les autorisations **Execute** uniquement par défaut.  
  
## <a name="evidence"></a>Preuve  
 Une preuve représente l'information que le Common Language Runtime (CLR) utilise pour définir une stratégie de sécurité relative aux assemblys de code. Une preuve indique au runtime que le code possède une caractéristique particulière. Les formes communes de preuve incluent les signatures numériques et l'emplacement d'un assembly. Une preuve peut également être personnalisée pour représenter d'autres informations ayant une importance pour l'application.  
  
 Les assemblys et les domaines d'applications reçoivent des autorisations sur la base de la preuve. Par exemple, l'emplacement d'un assembly auquel [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] tente d'accéder est une forme commune de preuve pour les assemblys portant un nom faible. Il s'agit d'une preuve d'URL. La preuve d'URL d'une extension pour le traitement des données personnalisée, qui est déployée sur un serveur de rapports, peut être « C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll ». Le nom fort ou la signature numérique d'un assembly est une autre forme commune de preuve. Dans ce cas, la preuve est représentée par les informations de clé publique d'un assembly.  
  
## <a name="code-groups"></a>Groupes de codes  
 Un groupe de codes est un regroupement logique de codes selon une condition particulière d'appartenance (membership). Tout code remplissant la condition d'appartenance est inclus dans le groupe. Les administrateurs configurent une stratégie de sécurité en gérant les groupes de codes et leurs jeux d'autorisations associés.  
  
 Une condition d'appartenance d'un groupe de codes est basée sur la preuve. Par exemple, une appartenance « URL » d'un groupe de codes est basée sur la preuve URL. Le Common Language Runtime (CLR) utilise des caractéristiques d'identification (par exemple la preuve d'URL) pour décrire le code et déterminer si une condition d'appartenance à un groupe a été remplie. Par exemple, si la condition d'appartenance d'un groupe de codes est « code dans l'assembly C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll », le runtime examine la preuve pour déterminer si le code provient de cet emplacement. Voici un exemple d'entrée de configuration pour ce type de groupe de codes :  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="FullTrust"  
   Name="MyCodeGroup"  
   Description="Code group for my data processing extension">  
      <IMembershipCondition class="UrlMembershipCondition"  
         version="1"  
         Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll"  
       />  
</CodeGroup>  
```  
  
 Contactez votre administrateur système ou votre expert en déploiement d'applications pour déterminer le type de sécurité d'accès du code et les groupes de codes requis par vos assemblys personnalisés ou extensions [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="named-permission-sets"></a>Jeux d'autorisations nommés  
 Un jeu d'autorisations nommé est un jeu d'autorisations que les administrateurs peuvent associer à un groupe de codes. La plupart des jeux d'autorisations nommés comprennent au moins une autorisation, un nom et une description pour le jeu d'autorisations. Les administrateurs peuvent utiliser des jeux d'autorisations nommés pour établir ou modifier la stratégie de sécurité des groupes de codes. Plusieurs groupes de codes peuvent être associés au même jeu d'autorisations nommé. Le CLR fournit des jeux d’autorisations nommés intégrés, par exemple **Nothing**, **Execution**, **Internet**, **LocalIntranet**, **Everything** et **FullTrust**.  
  
> [!NOTE]  
>  Les extensions relatives aux données personnalisées, à la remise, au rendu et à la sécurité dans [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] doivent s’exécuter sous le jeu d’autorisations **FullTrust**. Contactez votre administrateur système pour ajouter le groupe de codes et les conditions d'appartenance appropriés pour vos extensions [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 Vous pouvez associer vos propres niveaux personnalisés d'autorisations pour les assemblys personnalisés que vous utilisez avec des rapports. Par exemple, si vous souhaitez permettre à un assembly d'accéder à un fichier spécifique, vous pouvez créer un jeu d'autorisations nommé disposant d'un accès d'E/S de fichier spécifique, puis assigner ce jeu d'autorisations à votre groupe de codes. Le jeu d'autorisations suivant accorde l'accès en lecture seule au fichier MyFile.xml :  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="MyNewFilePermissionSet"  
   Description="A special permission set that grants read access to my file.">  
    <IPermission class="FileIOPermission"  
       version="1"  
       Read="C:\MyFile.xml"/>  
    <IPermission class="SecurityPermission"  
       version="1"  
       Flags="Assertion, Execution"/>  
</PermissionSet>  
```  
  
 Voici un exemple de groupe de codes auquel vous accordez ce jeu d'autorisations :  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="MyNewFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\MyCustomAssembly.dll"/>  
</CodeGroup>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Reporting Services de &#40;de développement sécurisé&#41;](secure-development-reporting-services.md)  
  
  
