---
title: "Notes de mise à jour de SQL Server 2017 | Documents Microsoft"
ms.custom: 
ms.date: 05/16/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
caps.latest.revision: 41
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 67c1c0f3a9da6cc5d050da5db8a493f5da934c2a
ms.openlocfilehash: fa45fea4ebb378f035b4b4af2b1fa8a20bc152a5
ms.contentlocale: fr-fr
ms.lasthandoff: 06/23/2017

---
# <a name="sql-server-2017-release-notes"></a>Notes de mise à jour de SQL Server 2017
Cette rubrique décrit les limitations et les problèmes de [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)]. Pour des informations connexes, consultez les rubriques suivantes :

- [Quelles sont les nouveautés dans SQL Server 2017](../sql-server/what-s-new-in-sql-server-2017.md).
- [SQL Server sur Linux notes de publication](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-release-notes).
- [Notes de publication de SQL Server Reporting Services](../reporting-services/reporting-services-release-notes.md).

 **Essayez-le :**    
   -   [![Télécharger à partir du Centre d’évaluation](../analysis-services/media/download.png)](http://go.microsoft.com/fwlink/?LinkID=829477)  Télécharger [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] à partir du **[Centre d’évaluation](http://go.microsoft.com/fwlink/?LinkID=829477)**

## <a name="sql-server-2017-ctp-21-may--2017"></a>SQL Server CTP 2017 2.1 (mai 2017)
### <a name="documentation-ctp-21"></a>Documentation (préliminaire CTP 2.1)
- **Problème et impact sur le client :** la documentation pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est limitée, et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Dans les articles, le contenu propre à [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est noté avec **S’applique à**. 
- **Problème et impact sur le client :** aucun contenu hors connexion n’est disponible pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="sql-server-reporting-services-ctp-21"></a>SQL Server Reporting Services (CTP 2.1)

- **Impact sur le problème et le client :** si vous disposez de SQL Server Reporting Services et Power BI serveur de rapports sur le même ordinateur et désinstaller un d’eux, vous ne serez n’est plus en mesure de se connecter au serveur de rapports avec le Gestionnaire de Configuration de Report Server restants.
- **Solution de contournement** pour contourner ce problème, vous devez effectuer les opérations suivantes après la désinstallation d’un des serveurs.

    1. Lancez une invite de commandes en mode administrateur.
    2. Accédez au répertoire où est installé le serveur de rapports restants.

        *Emplacement par défaut pour le serveur de rapports Power BI : serveur de rapports de C:\Program Files\Microsoft Power BI*

        *Emplacement par défaut pour SQL Server Reporting Services : C:\Program Files\Microsoft SQL Server Reporting Services*

    3. Puis accédez au dossier suivant. Il s’agit de *SSRS* ou *PBIRS* selon ce qui est restant.
    4. Accédez au dossier WMI.
    5. Exécutez la commande suivante :

        ```
        regsvr32 /i ReportingServicesWMIProvider.dll
        ```

        Vous pouvez ignorer l’erreur suivante, si elle s’affiche.

        ```
        The module "ReportingServicesWMIProvider.dll" was loaded but the entry-point DLLInstall was not found. Make sure that "ReportingServicesWMIProvider.dll" is a valid DLL or OCX file and then try again.
        ```

### <a name="tsqllanguageservicemsi-ctp-21"></a>TSqlLanguageService.msi (CTP 2.1)

- **Impact sur le problème et le client :** après l’installation sur un ordinateur qui possède une version 2016 de *TSqlLanguageService.msi* (via le programme d’installation de SQL ou installé en tant que composant redistribuable autonome) les versions v13.* (SQL 2016) de *Microsoft.SqlServer.Management.SqlParser.dll* et *Microsoft.SqlServer.Management.SystemMetadataProvider.dll* sont supprimés. Toutes les applications qui ont une dépendance sur les versions de 2016 de ces assemblys puis cesse de fonctionner, ce qui donne une erreur similaire à : *erreur : Impossible de charger le fichier ou l’assembly ' Microsoft.SqlServer.Management.SqlParser, Version = 13.0.0.0, Culture = neutral, PublicKeyToken = 89845dcd8080cc91' ou une de ses dépendances. Le système ne peut pas trouver le fichier spécifié.*

   En outre, tente de réinstaller une version 2016 de TSqlLanguageService.msi échouera avec le message : *Échec de l’Installation de Microsoft SQL Server 2016 T-SQL Language Service, car une version supérieure existe déjà sur l’ordinateur*.

- **Solution de contournement** pour contourner ce problème et de corriger une application qui dépend de la v13 version des assemblys, procédez comme suit :

   1. Accédez à **Ajout/Suppression de programmes**
   1. Rechercher *Microsoft SQL Server vNext T-SQL Language Service CTP2.1*, faites un clic droit, puis sélectionnez **désinstallation**.
   1. Une fois que le composant est supprimé, réparer l’application est interrompue (ou réinstallez la version appropriée de *TSqlLanguageService.MSI*)

   Cette solution de contournement supprimera la version v14 de ces assemblys, donc toutes les applications qui dépendent des versions v14 ne fonctionnera plus. Si ces assemblys sont nécessaires, une installation distincte sans les 2016 installations côte à côte est requise.

![horizontal_bar](../sql-server/media/horizontal-bar.png)
## <a name="sql-server-2017-ctp-20-april--2017"></a>SQL Server 2017 CTP 2.0 (avril 2017)
### <a name="documentation-ctp-20"></a>Documentation (CTP 2.0)
- **Problème et impact sur le client :** la documentation pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est limitée, et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Dans les articles, le contenu propre à [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est noté avec **S’applique à**. 
- **Problème et impact sur le client :** aucun contenu hors connexion n’est disponible pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="always-on-availability-groups"></a>Groupes de disponibilité Always On

- **Impact sur le problème et le client :** instance A SQL Server qui héberge un réplica secondaire du groupe de disponibilité se bloque si la version majeure de SQL Server est inférieure à l’instance qui héberge le réplica principal. Affecte des mises à niveau à partir de toutes les versions prises en charge de SQL Server qui hébergent des groupes de disponibilité pour SQL Server [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] CTP 2.0. Cela se produit dans les étapes suivantes. 

> 1. Utilisateur met à niveau SQL Server instance hébergement réplica secondaire conformément à [meilleures pratiques](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md).
> 2. Après la mise à niveau, un basculement se produit, et qui vient d’être mis à niveau secondaire devienne le réplica principal avant la fin de la mise à niveau pour tous les réplicas secondaires du groupe de disponibilité. L’ancien principal est désormais une base de données secondaire qui est une version inférieure à principal.
> 3. Le groupe de disponibilité est dans une configuration non prise en charge et tous les réplicas secondaires restants peuvent être vulnérables aux pannes. 

- **Solution de contournement** se connecter à l’instance de SQL Server qui héberge le nouveau réplica principal et supprimer le réplica secondaire défaillant à partir de la configuration.

   `ALTER AVAILABILITY GROUP agName REMOVE REPLICA ON NODE instanceName`

   Permet de récupérer l’instance de SQL Server hébergeant le réplica secondaire.


![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-14-march--2017"></a>SQL Server 2017 CTP 1.4 (mars 2017)

### <a name="documentation-ctp-14"></a>Documentation (CTP 1.4)
- **Problème et impact sur le client :** la documentation pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est limitée, et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Dans les articles, le contenu propre à [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est noté avec **S’applique à**. 
- **Problème et impact sur le client :** aucun contenu hors connexion n’est disponible pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-13-february--2017"></a>SQL Server CTP 2017 1.3 (février 2017)
### <a name="supported-installation-scenarios-ctp-13"></a>Scénarios d’installation pris en charge (CTP 1.3)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est destiné à une version d’évaluation uniquement.  Les déploiements de production ne sont pas pris en charge. Nous vous recommandons d’installer et de tester [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] sur une machine virtuelle.

### <a name="documentation-ctp-13"></a>Documentation (CTP 1.3)
- **Problème et impact sur le client :** la documentation pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est limitée, et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Dans les articles, le contenu propre à [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est noté avec **S’applique à**. 
- **Problème et impact sur le client :** aucun contenu hors connexion n’est disponible pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].

### <a name="sql-server-integration-services-ssis-ctp-13"></a>SQL Server Integration Services (SSIS) (CTP 1.3)
#### <a name="cdc-components-not-supported-in-this-ctp-release"></a>Composants CDC non pris en charge dans cette version CTP
-   **Problème et impact sur le client**: la tâche de contrôle CDC, la source CDC et le séparateur CDC ne sont pas pris en charge dans cette version CTP.
-   **Solution de contournement :**Il n’existe aucune solution de contournement.


![horizontal_bar](../sql-server/media/horizontal-bar.png)

## <a name="sql-server-2017-ctp-12-january--2017"></a>SQL Server CTP 2017 1.2 (janvier 2017)
### <a name="supported-installation-scenarios-ctp-12"></a>Scénarios d’installation pris en charge (CTP 1.2)
[!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est destiné à une version d’évaluation uniquement.  Les déploiements de production ne sont pas pris en charge. Nous vous recommandons d’installer et de tester [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] sur une machine virtuelle.

### <a name="sql-server-database-engine-ctp-12"></a>Moteur de base de données SQL Server (CTP 1.2)
- **Problème et impact sur le client :** dans certains cas, le service MSSQLSERVER se bloque à l’état « Démarrage ».
- **Solution de contournement :** pour contourner ce problème :
  -  Créez une dépendance entre le service `mssqlserver` et le service `keyiso` . Pour ce faire, vous pouvez exécuter la commande suivante à partir d’une invite de commandes avec élévation de privilèges : `sc config mssqlserver depend= keyiso`
  - Redémarrez l'ordinateur.

### <a name="documentation-ctp-12"></a>Documentation (CTP 1.2)
- **Problème et impact sur le client :** La documentation pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est limitée et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL15_md](../includes/sssql15-md.md)] .  Dans les articles, le contenu propre à [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] est noté avec **S’applique à :**. 
- **Problème et impact sur le client :** aucun contenu hors connexion n’est disponible pour [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)].
 
### <a name="sql-server-integration-services-ssis-ctp-12"></a>SQL Server Integration Services (SSIS) (CTP 1.2)
#### <a name="deleting-the-ssis-catalog-may-fail-when-ssis-scale-out-is-installed"></a>La suppression de catalogue SSIS peut échouer quand SSIS Scale Out est installé
**Problème et impact sur le client :**quand la fonctionnalité SSIS Scale Out est installée sur un ordinateur, la suppression de la base de données du catalogue SSISDB peut échouer avec l’erreur suivante : « Impossible de supprimer la connexion *“connexion”* , tant que l’utilisateur est connecté.
   
**Solution de contournement**:
-   Sur les ordinateurs Scale Out Master, exécutez la commande « services.msc » pour ouvrir la fenêtre Services. Arrêtez le service SQL Server Integration Services Cluster Master.
-   Sur les ordinateurs Scale Out Worker, qui se connectent au maître, exécutez la commande « services.msc » pour ouvrir la fenêtre Services. Arrêtez le service SQL Server Integration Services Cluster Worker.

Vous pouvez à présent supprimer la base de données de catalogue SSISDB.

### <a name="sql-server-master-data-services-ctp-12"></a>SQL Server Master Data Services (CTP 1.2)
#### <a name="transaction-may-not-work-when-the-entity-transaction-log-type-is-set-to-attribute"></a>Une transaction peut échouer quand le type de journal de transactions d’entités a la valeur Attribut
**Problème et impact sur le client :** Quand le type de journal de transactions d’entités a la valeur **Attribut** dans [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] (la valeur par défaut est **Membre**), les scénarios suivants échouent :

* Les transactions liées aux changements d’entités ne sont pas affichées dans le site web.
* Impossible d’ouvrir la page **Transactions** dans le site web et d’inverser une transaction.
* Impossible de mettre à jour une entité avec une annotation de transaction dans le site web.

**Solution de contournement :**Il n’existe aucune solution de contournement.

#### <a name="copy-version-may-not-work-when-copy-only-committed-version-is-set-to-false"></a>L’action Copier la version peut ne pas fonctionner quand **Copier uniquement les versions activées** a la valeur False
-  **Problème et impact sur le client :** Quand le paramètre **Copier uniquement les versions activées** a la valeur **Non** (la valeur par défaut est **Oui**), l’opération de copie de version peut échouer. Aucun message d’erreur n’est affiché.
-  **Solution de contournement :**Il n’existe aucune solution de contournement.

##  <a name="infotipsql-servermediainfo-tippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](../sql-server/media/info-tip.png) Contacter l’équipe d’ingénierie de SQL Server 
- [Dépassement de la capacité de la pile (balise sql-server) : poser des questions techniques](http://stackoverflow.com/questions/tagged/sql-server)
- [Forums MSDN : poser des questions techniques](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver)
- [Microsoft Connect : signaler des bogues et demander des fonctionnalités](https://connect.microsoft.com/SQLServer/Feedback)
- [Reddit : discussion générale sur R](https://www.reddit.com/r/SQLServer/)


![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)


