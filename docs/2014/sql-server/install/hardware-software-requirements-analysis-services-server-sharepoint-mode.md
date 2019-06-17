---
title: Matérielle et logicielle requise pour le serveur Analysis Services en Mode SharePoint (SQL Server 2014) | Microsoft Docs
ms.prod: sql-server-2014
ms.technology: database-engine
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.topic: conceptual
ms.custom: ''
ms.date: 06/13/2017
ms.openlocfilehash: ae38efa69921a2edf94f0e40c4505e345ca0015a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094953"
---
# <a name="hardware-and-software-requirements-for-analysis-services-server-in-sharepoint-mode-sql-server-2014"></a>Configurations matérielle et logicielle requises pour le serveur Analysis Services en mode SharePoint (SQL Server 2014)

[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] prend en charge SharePoint 2010 et SharePoint 2013. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2013 s'exécute en dehors de la batterie de serveurs SharePoint, bien qu'il puisse être installé sur des serveurs SharePoint. [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 s'exécute sur des serveurs d'applications dans une batterie de serveurs SharePoint 2010 et utilise les fonctionnalités et l'infrastructure SharePoint pour prendre en charge des opérations de serveur. Pour installer [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] pour l'une des versions de SharePoint, utilisez l'Assistant Installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Après l'installation, effectuez les opérations suivantes :  
  
- Exécutez la version appropriée de l'outil de configuration [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] pour la version de SharePoint.  
  
- Pour SharePoint 2013, installez le [installer ou désinstaller le PowerPivot pour SharePoint Add-in &#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).  

##  <a name="bkmk_sqleditions"></a> Configuration requise de SQL Server  
 Les fonctionnalités de Business Intelligence ne sont pas toutes disponibles dans toutes les éditions de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Pour plus d’informations, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) et [éditions et composants de SQL Server 2014](../editions-and-components-of-sql-server-2016.md).  
  
 Vous trouverez les notes de publication en cours dans [Notes de publication de Microsoft SQL Server 2014](https://go.microsoft.com/fwlink/?LinkID=296445).  
  

  
##  <a name="bkmk_sqllicense"></a> Gestionnaire de licences SQL Server  
 Pour plus d'informations sur les licences SQL Server, reportez-vous aux sites Web suivants :  
  
-   [Feuille de données SQL Server 2014 licences](https://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf) (https://download.microsoft.com/download/6/6/F/66FF3259-1466-4BBA-A505-2E3DA5B2B1FA/SQL_Server_2014_Licensing_Datasheet.pdf).  
  
-   [Comment acheter : Prise en charge des modèles de licences de SQL Server](https://www.microsoft.com/licensing/product-licensing/sql-server-2014?activetab=sql-server-2014-pivot%3aprimaryr2) (https://www.microsoft.com/licensing/product-licensing/sql-server-2014?activetab=sql-server-2014-pivot%3aprimaryr2).  
  
##  <a name="bkmk_ssas__sharepoint_2013"></a> Analysis Services est installé sur SharePoint 2013  
 Si vous installez le serveur Analysis Services en mode SharePoint seul sur un serveur, alors la configuration système minimale requise est basée sur [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] plutôt que sur la configuration requise pour SharePoint Server.  
  
 [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
 L'exécution de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint est optimale sur des serveurs professionnels de nouvelle génération qui offrent des seuils de RAM plus élevés et une plus grande capacité de traitement. De grandes quantités de mémoire RAM sont utilisées pour stocker les données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] en mémoire. La mémoire RAM prend en charge la capacité à s'adapter aux modifications structurelles. Des processeurs supplémentaires prennent en charge les analyses longue durée des données brutes, non agrégées. Les données assument leur structure dans un environnement dynamique, en réponse à une analyse de données pilotée par l'utilisateur et initialisée via un client Excel ou une interface frontale.  
  
> [!TIP]  
>  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint utilise les caches L2 et L3. Pour améliorer les performances, envisagez d'utiliser des processeurs avec des caches L2 et L3 de plus grande taille.  
  
 Le tableau suivant décrit la configuration matérielle minimale et recommandée pour un serveur autonome [!INCLUDE[ssGeminiShortvnext](../../includes/ssgeminishortvnext-md.md)] qui ne fait pas partie de la batterie de serveurs SharePoint :  
  
|Composant|Minimum|Recommandation|  
|---------------|-------------|-----------------|  
|Processeur|Processeur 64 bits à double noyau, 3 GHz|16 cœurs|  
|RAM|8 Go de RAM|64 Go de RAM|  
|Stockage|80 gigaoctets de stockage|80 gigaoctets ou plus|  
  
 Si vous installez le serveur Analysis Services en mode SharePoint sur un serveur de batterie SharePoint, reportez-vous à la configuration système minimale requise pour [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et SharePoint Server aux adresses suivantes :  
  
-   [Configurations matérielle et logicielle requises pour l’installation de SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md)  
  
-   [Configuration matérielle et logicielle requise pour SharePoint 2013](https://technet.microsoft.com/library/cc262485\(office.15\).aspx).  
  
 Les recommandations standard relatives au matériel et aux logiciels SharePoint 2013 valent pour une solution de gestion de documents basée sur le Web pour un groupe de travail ou une équipe. Étant donné que le traitement [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] consomme de grandes quantités de données, la recommandation standard est suffisante uniquement si la charge de travail globale est petite, par exemple, inférieure à 100 utilisateurs ou classeurs. Un déploiement de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] plus important nécessite davantage de puissance de calcul.  
  
##  <a name="bkmk_ssas__sharepoint_2010"></a> Analysis Services est installé sur un serveur SharePoint 2010  
 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 2010 s'exécute sur des serveurs d'applications dans une batterie de serveurs SharePoint 2010 et utilise les fonctionnalités et l'infrastructure SharePoint pour prendre en charge des opérations de serveur. Le tableau suivant récapitule les conditions requises liées à des déploiements de SharePoint 2010 :  
  
|Composant|Condition requise|  
|---------------|-----------------|  
|Version SharePoint|SharePoint 2010 Enterprise, avec Excel Services, le service Banque d'informations sécurisé et le service d'émission de jetons Revendications vers Windows configurés sur la même batterie de serveurs.<br /><br /> SharePoint doit être installé à l'aide de l'option Batterie de serveurs du programme d'installation de SharePoint (l'option d'installation autonome de SharePoint n'est pas prise en charge). [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] requiert l'infrastructure de batterie de serveurs pour pouvoir prendre en charge l'accès aux données et en tant qu'administrateur. L'installation autonome ne fournit pas ces services.<br /><br /> L'édition développeur, qui s'exécute sur Windows 7 ou Windows Vista, n'est pas prise en charge pour les installations serveur de [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)].|  
|Service Packs|Le Service Pack 1 (SP1) pour SharePoint Server 2010 est requis.<br /><br /> Le Service Pack 1 de SharePoint 2010 est requis pour les fonctionnalités [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)][!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)].<br /><br /> La mise à jour cumulative d'août 2010 pour SharePoint 2010, ou une version ultérieure, est requise lors de la mise à niveau d'une version antérieure de [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] vers [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]. La mise à jour cumulative d'août 2010, ou une version ultérieure, doit être installée après l'installation de SharePoint Service Pack 1. Une nouvelle installation de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ne nécessite pas la mise à jour cumulative. Pour plus d’informations, consultez [août 2010 mise à jour Cumulative pour SharePoint a été publié](http://blogs.technet.com/b/stefan_gossner/archive/2010/09/02/august-2010-cumulative-update-for-sharepoint-has-been-released.aspx).|  
|Application Web de SharePoint|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint 2010 ne prend en charge que les applications Web SharePoint configurées pour utiliser l'authentification en mode classique. Si vous ajoutez [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint à une batterie de serveurs existante, assurez-vous que l'application Web avec laquelle vous projetez de l'utiliser est configurée pour utiliser l'authentification en mode classique. Pour obtenir des instructions sur la façon de vérifier le mode d’authentification, consultez la section « Vérifiez que l’application Web utilise l’authentification du mode classique » dans [déployer des Solutions PowerPivot pour SharePoint](../../analysis-services/power-pivot-sharepoint/deploy-power-pivot-solutions-to-sharepoint.md).|  
|Fournisseurs de données requis pour l'actualisation des données [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] côté serveur|L'actualisation des données côté serveur répète les mêmes étapes d'extraction de données utilisées pour importer à l'origine les données. Cela signifie que les fournisseurs de données utilisés pour importer les données sur une station de travail cliente doivent également être présents sur le serveur [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] pour SharePoint.<br /><br /> De plus, l'utilisation de flux de données sur un serveur SharePoint requiert que vous ayez ADO.NET Data Services. Le programme d'installation préalable de SharePoint n'installe pas ce logiciel automatiquement. Les logiciels suivants doivent être installés manuellement.<br /><br /> Assemblys d'exécution ADO.NET Data Services 3.5 SP1, utilisés pour exporter une liste SharePoint en tant que flux de données. Téléchargez et installez la version qui correspond à votre système d'exploitation :<br /><br /> Pour Windows Server 2008 R2, utilisez [mise à jour de ADO.NET Data Services pour .NET Framework 3.5 SP1 pour Windows 7 et windows Server 2008 R2 (https://go.microsoft.com/fwlink/?LinkId=182557)](https://go.microsoft.com/fwlink/?LinkId=182557). Windows Server 2008 R2 **SP1** contient déjà le fournisseur mis à jour.<br /><br /> Pour Windows Server 2008, utilisez [mise à jour de ADO.NET Data Services pour .NET Framework 3.5 SP1 pour Windows 2000, Windows Server 2003, Windows XP, Windows Vista et Windows Server 2008 (https://go.microsoft.com/fwlink/?LinkId=158125)](https://www.microsoft.com/download/details.aspx?id=22734).|  
  
 [Déterminer la configuration matérielle et logicielle requise (SharePoint Server 2010) ()https://go.microsoft.com/fwlink/?LinkId=169734)](https://go.microsoft.com/fwlink/?LinkId=169734)  
  
## <a name="additional-information"></a>Informations supplémentaires  

Pour plus d’informations sur les modifications apportées à SharePoint, consultez [changements entre SharePoint 2010 vers SharePoint 2013](https://technet.microsoft.com/library/ff607742\(office.15\).aspx) (https://technet.microsoft.com/library/ff607742(office.15).aspx).