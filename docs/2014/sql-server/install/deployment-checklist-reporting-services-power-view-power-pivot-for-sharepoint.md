---
title: 'Liste de vérification du déploiement : Reporting Services, Power View et PowerPivot pour SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 9a2575c8-06fc-4ef4-9f24-c19e52b1bbcf
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: f1eb0f6892192e5ed328386e6730ec3b1c41f05b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "71952550"
---
# <a name="deployment-checklist-reporting-services-power-view-and-powerpivot-for-sharepoint"></a>Liste de vérification du déploiement : Reporting Services, Power View et PowerPivot pour SharePoint
  Utilisez la liste de vérification suivante pour installer ces fonctionnalités BI dans la même batterie de serveurs SharePoint : PowerPivot pour SharePoint, le Générateur de rapports et [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. Bien que cette liste de vérification recommande un ordre d'installation précis, dans la pratique vous pouvez installer ces fonctionnalités dans presque n'importe quel ordre. Cette liste de vérification suppose l'installation des produits ou des fonctionnalités suivants :  
  
1.  SharePoint Server 2010 avec Service Pack 1 (SP1)  
  
2.  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]Moteur de base de données  
  
3.  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Reporting Services et complément Reporting Services  
  
4.  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot pour SharePoint  
  
 Après avoir installé ces fonctionnalités, vous pouvez effectuer les opérations suivantes.  
  
-   Accédez aux classeurs PowerPivot que vous avez créés dans PowerPivot pour Excel depuis les sites SharePoint.  
  
-   Générez des rapports interactifs [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] sur la base de classeurs PowerPivot dans SharePoint.  
  
-   Créez des rapports lorsque vous lancez le Générateur de rapports dans SharePoint.  
  
> [!NOTE]  
>  PowerPivot pour SharePoint requiert l'installation de SharePoint 2010 Service Pack 1 (SP1) sur la batterie de serveurs SharePoint. Si vous installez le logiciel à des fins d'évaluation, pensez à démarrer avec un serveur propre afin d'éviter la surcharge de travail induite par l'étape de mise à niveau de la batterie de serveurs. La mise à niveau d'une batterie de serveurs a un impact non négligeable sur les opérations de SharePoint et exige généralement une planification méticuleuse. Si votre objectif est d'installer PowerPivot pour SharePoint aussi rapidement que possible, procédez comme suit : installez SharePoint 2010, installez le Service Pack 1 de SharePoint 2010, puis configurez la batterie. La mise à niveau est évitée, car la batterie de serveurs n'est pas encore configurée lorsque vous installez SharePoint 2010 SP1.  
>   
>  Dans cette liste de vérification, l'étape de configuration de la batterie est prise en compte lors de la configuration de PowerPivot pour SharePoint, à l'aide de l'outil de configuration de PowerPivot. Vous pouvez aussi utiliser l'Assistant Configuration de produit SharePoint si vous préférez cette approche. Les deux méthodes génèrent une batterie de serveurs opérationnelle prenant en charge PowerPivot pour SharePoint.  
  
## <a name="prerequisites"></a>Prérequis  
 Vous devez être administrateur local pour exécuter le programme d'installation de SQL Server.  
  
 SharePoint Server 2010 Enterprise Edition est requis pour PowerPivot pour SharePoint. Vous pouvez également utiliser l'édition Enterprise Evaluation.  
  
 SharePoint Server 2010 SP1 doit être installé. Sans lui, vous ne pouvez pas configurer la batterie de serveurs pour utiliser les fonctionnalités de [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] .  
  
 L'ordinateur doit être attaché à un domaine.  
  
 Vous devez avoir un ou plusieurs comptes d'utilisateur de domaine pour configurer les services. Vous aurez besoin de comptes d'utilisateur de domaine pour les services suivants : services Web SharePoint et services d'administration, Reporting Services, Analysis Services, Excel Services, services Banque d'informations sécurisés et le service système PowerPivot. Les comptes de domaine sont requis par la fonctionnalité de comptes gérés dans SharePoint. Le moteur de base de données peut être configuré à l'aide d'un compte virtuel, mais tous les autres services doivent être exécutés en tant qu'utilisateur de domaine.  
  
 Le nom de l'instance PowerPivot doit être disponible. Vous ne pouvez pas avoir une instance nommée existante PowerPivot sur l'ordinateur d'installation de PowerPivot pour SharePoint.  
  
 Si vous installez PowerPivot pour SharePoint sur une batterie de serveurs existante, vous devez avoir une ou plusieurs applications Web SharePoint configurées pour l'authentification en mode classique. L'accès aux données PowerPivot fonctionne uniquement si l'application Web prend en charge l'authentification en mode classique. Pour plus d'informations sur les exigences du mode classique, consultez [PowerPivot Authentication and Authorization](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-authentication-and-authorization).  
  
 Consultez les rubriques supplémentaires suivantes pour comprendre les exigences du système et des versions :  
  
-   [Instructions d'utilisation des fonctionnalités BI de SQL Server dans une batterie de serveurs SharePoint 2010](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
## <a name="steps"></a>Étapes  
 Les étapes suivantes impliquent qu'un administrateur procède à l'installation et à la configuration du serveur. L'utilisateur du programme d'installation de SharePoint est également administrateur de la batterie de serveur et souvent l'administrateur principal du site pour la collection de sites par défaut. Si vousrépartissez les étapes suivantes entre plusieurs personnes, des autorisations supplémentaires seront peut-être nécessaires pour le bon déroulement des étapes suivantes.  
  
|Étape|Lien|  
|----------|----------|  
|Exécutez l'Outil de préparation des produits SharePoint 2010.|Vous devez disposer du support d'installation pour SharePoint 2010. L'outil de préparation est PrerequisiteInstaller.exe sur le support d'installation.|  
|Installez l'édition SharePoint Server 2010 Enterprise ou Enterprise Evaluation.|Lors de l'installation de SharePoint, vous pouvez choisir de configurer la batterie de serveurs ultérieurement en vous abstenant d'exécuter l'Assistant Configuration des produits SharePoint 2010 une fois l'installation terminée. L’attente de la configuration de la batterie vous permettra d' [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] utiliser une instance de moteur de base de données, qui est installée dans une étape ultérieure, en tant que serveur de base de données de la batterie de serveurs. Pour configurer la batterie de serveurs, vous allez utiliser l'Outil de configuration PowerPivot. Il inclut des actions de configuration de la batterie de serveurs si celle-ci n'est pas encore configurée.|  
|Installer SharePoint Server 2010 SP1|Téléchargez SP1 à [https://support.microsoft.com/kb/2460045](https://go.microsoft.com/fwlink/p/?linkID=219697)partir de.|  
|Exécutez le programme d'installation [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pour installer le moteur de base de données et PowerPivot pour SharePoint.|[Installer PowerPivot pour SharePoint 2010](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)<br /><br /> L'étape 1 décrit l'installation de PowerPivot pour SharePoint. Dans cette étape, veillez à cliquer dans la case à cocher de la page Rôle d'installation qui ajoute le moteur de base de données au rôle. Cela ajoute le Moteur de base de données à votre installation afin que vous puissiez l’utiliser comme serveur de base de données de la batterie de serveurs lors de la configuration de la batterie de serveurs à l’étape suivante. Cependant, si la batterie est déjà configurée, vous pouvez ignorer cette étape.<br /><br /> L'étape 2 vous invite à configurer le serveur. Dans cette étape, choisissez l'Outil de configuration PowerPivot. Si plusieurs approches sont possibles, l'outil de configuration est la méthode la plus efficace pour une installation autonome.<br /><br /> Si SharePoint 2010 est installé mais pas configuré, l'outil pré-sélectionne les actions qui permettront de créer la batterie, une application Web par défaut et une collection de sites racine. Assurez-vous de garder ces options sélectionnées pour créer la batterie. Si vous avez déjà configuré la batterie, l'outil omettra ces actions pour offrir uniquement les actions nécessaires à la configuration de PowerPivot pour SharePoint.<br /><br /> L'étape 3 décrit l'installation de la version SQL Server 2008 R2 du fournisseur OLE DB Analysis Services. Cette étape est importante pour la prise en charge des versions d'un classeur créées dans la version 2008 R2 de PowerPivot pour Excel.|  
|Vérifiez que la batterie est opérationnelle.|D'abord, démarrez l'Administration centrale et confirmez sa disponibilité. Ensuite, ouvrez le site d’équipe en http://localhostentrant.  Vous devez voir un site d'équipe SharePoint.|  
|Vérifiez que PowerPivot pour SharePoint est opérationnel.|[Vérifier une installation PowerPivot pour SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/verify-a-power-pivot-for-sharepoint-installation)<br /><br /> Cette tâche confirme l'accès aux données PowerPivot à l'aide d'un classeur-exemple que vous téléchargez vers le serveur.|  
|Exécutez le programme d'installation [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] pour installer et configurer Reporting Services et le complément Reporting Services.|[Installer Reporting Services mode SharePoint pour SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)<br /><br /> Éventuellement, lors de l'installation de Reporting Services, vous pouvez ajouter une instance Analysis Services supplémentaire à l'arborescence de fonctionnalités de programme d'installation si vous souhaitez une deuxième ressource pour héberger les données tabulaires. L'instance supplémentaire Analysis Services est utilisée pour héberger les bases de données au modèle tabulaire créées dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Les bases de données tabulaires sont une source de données valide pour les rapports [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].<br /><br /> [Installer Analysis Services en mode tabulaire](https://docs.microsoft.com/analysis-services/instances/install-windows/install-analysis-services)|  
|Vérifiez que Reporting Services est opérationnel.|[Vérifier une installation de Reporting Services](../../reporting-services/install-windows/verify-a-reporting-services-installation.md)|  
|(Administrateurs de site) Configurez les autorisations SharePoint.|Les autorisations Collaboration sont requises pour l'ajout, la modification ou la suppression d'éléments dans les bibliothèques SharePoint. Le niveau d'autorisation d'affichage est suffisant pour l'accès en lecture seule aux rapports et aux classeurs PowerPivot qui présentent des données incorporées.<br /><br /> Les classeurs PowerPivot qui sont accessibles en tant que sources de données externes (où l'URL du classeur est une chaîne de connexion dans un autre classeur ou rapport) requièrent des autorisations de lecture, un niveau plus élevé que les autorisations d'affichage.<br /><br /> Autorisations de lecture également requises pour les connexions de modèle sémantique BI. Vous devrez peut-être créer de nouveaux niveaux d'autorisation ou groupes SharePoint pour mettre en place les autorisations appropriées.|  
|(Administrateurs de site) Étendez les bibliothèques de documents|Étendez les bibliothèques de documents aux types de contenu de BI : connexions de modèle sémantique BI, sources de données partagées de Reporting Services, rapports du Générateur de rapports :<br /><br /> 1) <br />                    **Activez la gestion des types de contenu**. Dans Documents partagés ou une autre bibliothèque de documents, sous l’onglet Bibliothèque, cliquez sur paramètres de la **bibliothèque**. Sous paramètres généraux, cliquez sur **Paramètres avancés**. Dans types de contenu, sélectionnez **Oui** pour autoriser la gestion des types de contenu, puis cliquez sur **OK**.<br /><br /> 2) <br />                    **Sélectionnez les types de contenu bi**. Sous l’onglet Bibliothèque, cliquez sur paramètres de la **bibliothèque**. Sous types de contenu, cliquez sur **Ajouter à partir de types de contenu de site existants**. À partir du groupe de types de contenu Business Intelligence, ajoutez le **fichier de connexion de modèle sémantique bi** et la **source de données du rapport**. Éventuellement, vous pouvez également ajouter d'autres types de contenu Reporting Services, tels que le modèle de rapport, pour activer des scénarios supplémentaires de création de rapport.<br /><br /> <br /><br /> Pour plus d’informations, consultez [Ajouter un type de contenu de connexion de modèle sémantique bi à une bibliothèque &#40;PowerPivot pour SharePoint&#41;](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/add-bi-semantic-model-connection-content-type-to-library) et [Ajouter des types de contenu de serveur de rapports à une bibliothèque &#40;Reporting Services en Mode intégré SharePoint&#41;](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md).|  
|(Administrateurs de site) Créez des fichiers de connexion de données utilisés pour lancer [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].|Vous devez créer une connexion de modèle sémantique BI (.bism) ou une source de données partagée Reporting Services (.rsds) comme source de données pour [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]. Après avoir créé un fichier de connexion de données, vous pouvez lancer [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] avec la connexion de données comme source de données.<br /><br /> [Créer une connexion de modèle sémantique BI à un classeur PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/create-a-bi-semantic-model-connection-to-a-power-pivot-workbook)<br /><br /> [Créer une connexion de modèle sémantique BI à une base de données model tabulaire](../../relational-databases/databases/model-database.md)<br /><br /> Remarque : [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] est disponible parce que vous avez installé la version [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] de Reporting Services et configuré le serveur en tant que service partagé. Si vous avez installé Reporting Services et si vous l'avez configuré pour le niveau d'intégration SQL Server 2008, [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] n'est pas disponible.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités prises en charge par les éditions de SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473)  
  
  
