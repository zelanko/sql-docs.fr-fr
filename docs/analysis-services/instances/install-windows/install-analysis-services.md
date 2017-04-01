---
title: "Installer Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/20/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cd6ac80d-b735-4e3e-a024-489f1409ad33
caps.latest.revision: 20
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 19
---
# Installer Analysis Services
  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est un serveur de base de données analytique hébergeant des modèles tabulaires, des cubes multidimensionnels et des modèles d’exploration de données auxquels vous pouvez accéder à partir de rapports, de feuilles de calcul et de tableaux de bord.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est multi-instance, ce qui signifie que vous pouvez installer plusieurs copies de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sur un seul ordinateur, ou exécuter des versions anciennes et nouvelles côte à côte. Les instances que vous installez sont exécutées dans un des trois modes, selon ce que vous avez spécifié pendant l’installation : multidimensionnel et exploration de données, tabulaire ou SharePoint. Si vous souhaitez utiliser plusieurs modes, vous devez avoir une instance distincte pour chacun.  
  
 Après avoir installé le serveur dans un mode donné, vous pouvez l’utiliser pour héberger des solutions conformes à ce mode. Par exemple, un serveur en mode tabulaire est indispensable si vous souhaitez accéder aux données du modèle tabulaire par le réseau.  
  
## Obtenir les outils et les concepteurs  
 Le programme d’installation de SQL Server n’installe plus les concepteurs de modèles ou les outils de gestion utilisés pour la conception de solutions ou l’administration de serveurs. Dans cette version, les outils ont une installation distincte, que vous pouvez obtenir à partir des liens suivants :  
  
-   [Télécharger SQL Server Management Studio pour SQL Server 2016](https://msdn.microsoft.com/en-US/library/mt238290.aspx)  
  
-   [Télécharger SQL Server Data Tools pour SQL Server 2016](https://msdn.microsoft.com/en-US/library/mt204009.aspx)  
  
 Vous aurez besoin de Management Studio et SQL Server Data Tools pour travailler avec des données et des instances d’Analysis Services. Vous pouvez installer les outils n’importe où, mais veillez à configurer des ports sur le serveur avant de tenter une connexion. Pour plus d'informations, consultez [Configure the Windows Firewall to Allow Analysis Services Access](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) .  
  
## Installer à l’aide d’un assistant  
 La liste suivante montre les pages de l’assistant Installation de SQL Server utilisées pour installer Analysis Services :  
  
1.  Sélectionnez **Analysis Services** dans l'Arborescence de fonctionnalités dans l'Installation.  
  
     ![Setup feature tree showing Analsyis Services](../../../analysis-services/instances/install-windows/media/ssas-setupas.gif "Setup feature tree showing Analsyis Services")  
  
2.  Dans la page Configuration d’Analysis Services, veillez à sélectionner **Mode Tabulaire** si vous voulez une instance tabulaire. Sinon, la valeur par défaut est **Mode multidimensionnel et d’exploration de données**.  
  
     ![Setup page with Analysis Services config options](../../../analysis-services/instances/install-windows/media/ssas-setupasconfig.png "Setup page with Analysis Services config options")  
  
 Le mode multidimensionnel et d’exploration de données utilise MOLAP comme stockage par défaut pour les modèles déployés dans Analysis Services. Après avoir déployé sur le serveur, vous pouvez configurer une solution pour utiliser ROLAP si vous souhaitez exécuter des requêtes directement sur la base de données relationnelle plutôt que de stocker les données de la requête dans une base de données multidimensionnelle Analysis Services.  
  
 Le mode tabulaire utilise le moteur d'analyse en mémoire xVelocity (VertiPaq), qui est le stockage par défaut pour les modèles tabulaires que vous déployez dans Analysis Services. Après le déploiement des solutions de modèle tabulaire sur le serveur, vous pouvez configurer les solutions tabulaires de manière sélective pour qu'elles utilisent le stockage sur disque de DirectQuery comme alternative au stockage gourmand en mémoire.  
  
 La gestion de la mémoire et les paramètres d’E/S peuvent être ajustés pour obtenir de meilleures performances lors de l’utilisation des modes de stockage qui ne sont pas définis par défaut. Pour plus d’informations, consultez [Propriétés du serveur dans Analysis Services](../../../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
## Installation à partir de ligne de commande  
 L’installation de SQL Server inclut un paramètre (**ASSERVERMODE**) qui spécifie le mode serveur. L'exemple suivant illustre une installation par ligne de commande qui installe Analysis Services en mode serveur tabulaire.  
  
```  
  
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /FEATURES=AS /ASSERVERMODE=TABULAR /INSTANCENAME=ASTabular /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 **INSTANCENAME** doit contenir moins de 17 caractères.  
  
 Toutes les valeurs de compte de l'espace réservé doivent être remplacées par des comptes valides et un mot de passe.  
  
 La casse est prise en compte pour **ASSERVERMODE**.  Toutes les valeurs doivent être exprimées en majuscules. Le tableau suivant décrit les valeurs valides pour **ASSERVERMODE**.  
  
|Valeur|Description|  
|-----------|-----------------|  
|MULTIDIMENSIONAL|Ceci est la valeur par défaut. Si vous ne définissez pas **ASSERVERMODE**, le serveur est installé en mode serveur multidimensionnel.|  
|POWERPIVOT|Cette valeur est facultative. En pratique, si vous définissez le paramètre **ROLE** , le mode serveur est automatiquement défini sur 1, ce qui rend **ASSERVERMODE** facultatif pour une installation de [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] pour SharePoint. Pour plus d’informations, consultez [Installer Power Pivot à partir de l’invite de commandes](http://msdn.microsoft.com/fr-fr/7f1f2b28-c9f5-49ad-934b-02f2fa6b9328).|  
|TABULAR|Cette valeur est obligatoire si vous installez Analysis Services en mode tabulaire à partir de la ligne de commande.|  
  
## Voir aussi  
 [Déterminer le mode serveur d'une instance Analysis Services](../../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)   
 [Convertir une base de données tabulaire en mémoire en DirectQuery dans SQL Server Management Studio &#40;SSMS&#41;](../Topic/Convert%20an%20in-memory%20Tabular%20Database%20to%20DirectQuery%20in%20SQL%20Server%20Management%20Studio%20\(SSMS\).md)   
 [Modélisation tabulaire &#40;SSAS&#41;](../Topic/Tabular%20Modeling%20\(SSAS\).md)  
  
  