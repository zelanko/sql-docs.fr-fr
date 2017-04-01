---
title: "Sp&#233;cifier des connexions pour des extensions de traitement de donn&#233;es personnalis&#233;es | Microsoft Docs"
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
  - "extensions pour le traitement des données personnalisées [Reporting Services]"
  - "IDbConnection (interface), chaînes de connexion"
  - "emprunt d'identité [Reporting Services]"
  - "IDbConnectionExtension (interface), chaînes de connexion"
  - "sources de données [Reporting Services], sécurité"
  - "chaînes de connexion [Reporting Services]"
  - "informations d'identification [Reporting Services]"
  - "authentification [Reporting Services]"
  - "sources de données externes [Reporting Services]"
  - "extensions pour le traitement des données [Reporting Services], connexions"
ms.assetid: 2cddc9ea-0e28-4350-80ae-332412908e47
caps.latest.revision: 20
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 20
---
# Sp&#233;cifier des connexions pour des extensions de traitement de donn&#233;es personnalis&#233;es
  Vous pouvez créer des extensions pour le traitement des données personnalisées ou utiliser des extensions tierces sur un serveur de rapports, soit pour améliorer la capacité de traitement des sources de données prises en charge, soit pour prendre en charge des types de données supplémentaires qui ne sont pas disponibles dans une installation [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] par défaut. Les connexions sont traitées différemment en fonction de l'implémentation. Les implémentations suivantes sont disponibles pour les extensions de traitement de données :  
  
-   Fournisseurs de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] personnalisés (si vous accédez à des données provenant de sources de données DB2.NET, Oracle, ODP.NET ou Teradata, vous pouvez utiliser un fournisseur de données .NET personnalisé)  
  
-   Les extensions de traitement de données personnalisées qui prennent en charge <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>  
  
-   Les extensions de traitement de données personnalisées qui prennent en charge <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>  
  
> [!NOTE]  
>  Demandez à votre fournisseur tiers comment votre extension de traitement de données personnalisée est implémentée.  
  
## Emprunt d'identité et extensions de traitement de données personnalisées  
 Si votre extension de traitement de données personnalisée se connecte à des sources de données utilisant l’emprunt d’identité, vous devez utiliser la méthode Open sur les interfaces <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> ou <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> pour effectuer la demande. Vous pouvez également stocker l’objet d’identité utilisateur (System.Security.Principal.WindowsIdentity), puis le réutiliser dans d’autres API d’extension de traitement de données.  
  
 Dans les versions antérieures de [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], toutes les extensions pour le traitement des données personnalisées étaient appelées via un emprunt d'identité utilisateur. Dans cette version, seule la méthode Open est appelée lors de l’emprunt de l’identité utilisateur. Si vous avez une extension de traitement de données existante nécessitant une sécurité intégrée, vous devez modifier votre code de manière à utiliser la méthode Open ou stocker l’objet d’identité utilisateur.  
  
## Connexions pour les fournisseurs de données .NET Framework personnalisés  
 Lorsque vous configurez une source de données spécifique, vous définissez des propriétés qui déterminent le type de source de données, la chaîne de connexion et les informations d'identification qui sont utilisées pour accéder à la source de données. Le tableau suivant décrit les types d'informations d'identification qui sont pris en charge pour les fournisseurs de données [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] . Pour plus d’informations sur la définition des propriétés de la source de données de rapport, consultez [Spécifier des informations d’identification et de connexion pour les sources de données de rapport](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md).  
  
|Informations d'identification|Connexions|  
|-----------------|-----------------|  
|Sécurité intégrée|Si votre fournisseur de données la prend en charge, vous pouvez utiliser la sécurité intégrée Windows. La demande est envoyée en utilisant les informations d'identification de l'utilisateur actuel.<br /><br /> Lors de la définition de la chaîne de connexion, n’oubliez pas d’inclure les arguments qui spécifient une sécurité intégrée (par exemple, une connexion à une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut inclure **Integrated Security=SSPI** dans la chaîne de connexion).|  
|Authentification Windows|Si votre fournisseur de données le prend en charge, vous pouvez utiliser un compte d'utilisateur de domaine Windows. Le serveur de rapports emprunte l'identité du compte d'utilisateur avant l'appel de l'extension de traitement de données.<br /><br /> Lors de la définition de la chaîne de connexion, n’oubliez pas d’inclure les arguments qui spécifient une sécurité intégrée (par exemple, une connexion à une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut inclure **Integrated Security=SSPI** dans la chaîne de connexion).|  
|Informations d'identification de la base de données|L'authentification de la base de données n'est pas prise en charge pour les connexions établies au moyen d'un fournisseur de données .NET personnalisé. Dans tous les cas, le serveur de rapports ne pourra pas établir la connexion.|  
|Ne pas demander les informations d'identification|Vous pouvez utiliser l'option Ne pas demander les informations d'identification avec les fournisseurs de données .NET personnalisés. Si le compte d'exécution sans assistance est spécifié, la chaîne de connexion détermine les informations d'identification qui sont utilisées. Le serveur de rapports emprunte l'identité du compte d'exécution sans assistance pour établir la connexion.<br /><br /> Si le compte d'exécution sans assistance n'est pas défini, le serveur de rapports ne peut pas établir la connexion. Pour plus d’informations sur la définition du compte, consultez [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).|  
  
## Connexions pour IDbConnection  
 Si vous utilisez une extension de traitement de données personnalisée qui prend uniquement en charge <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>, vous devez spécifier la connexion de cette façon :  
  
1.  Configurer le compte d'exécution sans assistance. La configuration de ce compte est requise pour les connexions établies à l'aide de **IDbConnection**. Le serveur de rapports emprunte l'identité du compte lors de l'établissement de la connexion.  
  
2.  Configurez les propriétés de la source de données sur le rapport de façon à utiliser **Ne pas demander les informations d'identification**.  
  
3.  Incluez dans la chaîne de connexion les informations d'identification utilisées pour établir une connexion à la source de données.  
  
 Lors de l'utilisation d' **IDbConnection**, les types d'informations d'identification suivants ne sont pas pris en charge : sécurité intégrée, comptes d'utilisateur Windows et informations d'identification de base de données. Si la connexion à la source de données utilise ces options, la connexion échoue sur le serveur de rapports.  
  
## Connexions pour IDbConnectionExtension  
 Si vous utilisez une extension de traitement de données personnalisée qui prend en charge <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>, vous pouvez spécifier la connexion de différentes façons :  
  
|Informations d'identification|Connexions|  
|-----------------|-----------------|  
|Sécurité intégrée|Si votre fournisseur de données la prend en charge, vous pouvez utiliser la sécurité intégrée Windows avec des extensions de traitement de données personnalisées qui utilisent **IDbConnectionExtension**.<br /><br /> Lors de la définition de la chaîne de connexion, n’oubliez pas d’inclure les arguments qui spécifient une sécurité intégrée (par exemple, une connexion à une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut inclure **Integrated Security=SSPI** dans la chaîne de connexion).|  
|Authentification Windows|Si votre fournisseur de données le prend en charge, vous pouvez utiliser un compte d'utilisateur de domaine Windows avec des extensions de traitement de données personnalisées qui utilisent **IDbConnectionExtension**.<br /><br /> Le serveur de rapports emprunte l'identité du compte d'utilisateur avant l'appel de l'extension de traitement de données. Lors de la définition de la chaîne de connexion, n’oubliez pas d’inclure les arguments qui spécifient une sécurité intégrée (par exemple, une connexion à une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut inclure **Integrated Security=SSPI** dans la chaîne de connexion).|  
|Informations d'identification de la base de données|Vous pouvez utiliser l'authentification de base de données pour configurer des connexions pour des extensions de traitement de données personnalisées qui utilisent **IDbConnectionExtension**.|  
|Ne pas demander les informations d'identification|Si le compte d'exécution sans assistance est spécifié, la chaîne de connexion détermine les informations d'identification qui sont utilisées.<br /><br /> Si le compte d'exécution sans assistance n'est pas défini, le serveur de rapports ne peut pas établir la connexion.|  
  
## Voir aussi  
 [Configurer le compte d’exécution sans assistance &#40;Gestionnaire de configuration de SSRS&#41;](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)   
 [Spécifier des informations d'identification et de connexion pour les sources de données de rapport](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Connexions de données, sources de données et chaînes de connexion &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Implémentation d'une extension pour le traitement des données](../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Gestionnaire de rapports &#40;SSRS en mode natif&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)   
 [Créer, supprimer ou modifier une source de données partagée &#40;Gestionnaire de rapports&#41;](../Topic/Create,%20Delete,%20or%20Modify%20a%20Shared%20Data%20Source%20\(Report%20Manager\).md)   
 [Configurer les propriétés de la source de données d’un rapport &#40;Gestionnaire de rapports&#41;](../../reporting-services/report-data/configure-data-source-properties-for-a-report-report-manager.md)  
  
  