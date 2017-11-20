---
title: "Quel &#39; nouveauté dans Integration Services dans SQL Server 2017 | Documents Microsoft"
ms.custom: 
ms.date: 09/28/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e26d7884-e772-46fa-bfdc-38567fe976a1
caps.latest.revision: 4
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: e76675099ab290d29231d434eb74e92b613185b7
ms.openlocfilehash: 63aba0f64bc63a3a86e5aa07245375938acdf6e4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/29/2017

---
# <a name="what39s-new-in-integration-services-in-sql-server-2017"></a>Quel &#39; nouveauté dans Integration Services dans SQL Server 2017
Cette rubrique décrit les fonctionnalités qui ont été ajoutées ou mises à jour dans [!INCLUDE[ssSQLv14_md](../includes/sssqlv14-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].

>   [!NOTE]
> SQL Server 2017 inclut également les fonctionnalités de SQL Server 2016 et les fonctionnalités ajoutées dans les mises à jour de SQL Server 2016. Pour plus d’informations sur les nouvelles fonctionnalités SSIS dans SQL Server 2016, consultez [Nouveautés d’Integration Services dans SQL Server 2016](../integration-services/what-s-new-in-integration-services-in-sql-server-2016.md).

## <a name="highlights-of-this-release"></a>Caractéristiques de cette version

Voici les nouvelles fonctionnalités d’Integration Services dans SQL Server 2017 plus importantes.

-   **Montée en puissance parallèle**. Distribuer l’exécution du package SSIS plus facilement sur plusieurs ordinateurs de travail et gérer des exécutions et des threads de travail à partir d’un seul ordinateur maître. Pour plus d’informations, consultez [Integration Services monter en charge](../integration-services/scale-out/integration-services-ssis-scale-out.md).

-   **Services d’intégration sur Linux**. Exécuter des packages SSIS sur les ordinateurs Linux. Pour plus d’informations, consultez [extraction, transformation et charger des données sur Linux avec SSIS](../linux/sql-server-linux-migrate-ssis.md).

-   **Améliorations de la connectivité**. Se connecter aux flux OData de Microsoft Dynamics AX Online et Microsoft Dynamics CRM Online avec les composants d’OData mis à jour. 

## <a name="new-in-azure-data-factory"></a>Nouveau dans Azure Data Factory

Avec la version préliminaire publique d’Azure Data Factory version 2 en septembre 2017, vous pouvez désormais effectuer les opérations suivantes :
-   Déployer des packages à la base de données de catalogue SSIS (SSISDB) sur la base de données SQL Azure.
-   Exécuter des packages déployés sur Azure sur le Runtime d’intégration de Azure-SSIS, un composant d’Azure Data Factory version 2.

Pour plus d’informations, consultez [courbes d’élévation et l’équipe SQL Server Integration Services les charges de travail dans le cloud](lift-shift/ssis-azure-lift-shift-ssis-packages-overview.md).

Ces nouvelles fonctionnalités requièrent 17,2 ou version ultérieure de SQL Server Data Tools (SSDT), mais ne nécessitent pas de SQL Server 2017 ou SQL Server 2016. Lorsque vous déployez des packages vers Azure, l’Assistant de déploiement de Package met toujours à niveau les packages au format de package plus récente.

## <a name="new-in-the-azure-feature-pack"></a>Nouveau dans le Feature Pack Azure

Outre les améliorations de connectivité dans SQL Server, l’Integration Services Feature Pack pour Azure a ajouté la prise en charge pour Azure Data Lake Store. Pour plus d’informations, voir le blog [nouveau Azure fonctionnalité Pack version renforcement ADLS connectivité](https://blogs.msdn.microsoft.com/ssis/2017/08/29/new-azure-feature-pack-release-strengthening-adls-connectivity/). Consultez également [Azure Feature Pack pour Integration Services (SSIS)](azure-feature-pack-for-integration-services-ssis.md).

## <a name="new-in-sql-server-data-tools-ssdt"></a>Nouveautés de SQL Server Data Tools (SSDT)

Vous pouvez maintenant développer des projets SSIS et des packages qui ciblent des versions de SQL Server 2012 via 2017 dans Visual Studio 2017 ou dans Visual Studio 2015. Pour plus d’informations, consultez [Télécharger SSDT (SQL Server Data Tools)](../ssdt/download-sql-server-data-tools-ssdt.md).

## <a name="new-in-ssis-in-sql-server-2017-rc1"></a>Nouveau dans SSIS dans SQL Server 2017 RC1

### <a name="new-and-changed-features-in-scale-out-for-ssis"></a>Fonctionnalités nouvelles et modifiées dans monter en charge de SSIS

-   Scale Out Master prend désormais en charge la haute disponibilité. Vous pouvez activer Always On pour SSISDB et définir Windows Server clustering de basculement pour le serveur qui héberge le service de mise à l’échelle des Master. En appliquant cette modification à l’échelle des maître, vous évitez d’un point de défaillance unique et fournissez une haute disponibilité pour le déploiement complet monter en charge.
-   La gestion de basculement des journaux d’exécution des Scale Out Workers est améliorée. Les journaux d’exécution sont conservées sur le disque local dans le cas où le montée en puissance des processus de travail après un arrêt inattendu. Une version ultérieure, lorsque le processus de travail redémarre, il recharge les journaux persistantes et continue à les enregistrer dans SSISDB.
-   Le paramètre *runincluster* de la procédure stockée **[catalog].[create_execution]** est renommé en *runinscaleout* pour des raisons de cohérence et de lisibilité. Ce changement de nom de paramètre a l’impact suivant :
    -   Si vous devez exécuter des packages dans monter en charge les scripts existants, vous devez modifier le nom du paramètre à partir de *runincluster* à *runinscaleout* pour utiliser les scripts dans la version RC1.
    -   SQL Server Management Studio (SSMS) 17.1 et les versions antérieures ne peuvent pas déclencher l’exécution du package dans la montée en puissance parallèle dans RC1. Le message d’erreur est : « *@runincluster* n’est pas un paramètre valide pour la procédure **create_execution** ». Ce problème est résolu dans la prochaine version de SSMS, la version 17.2. 17,2 et versions ultérieures de SSMS prennent en charge l’exécution de nom et le package nouveau paramètre de monter en charge. Jusqu'à ce que SSMS version 17,2 est disponible, comme une solution de contournement, vous pouvez utiliser votre version existante de SSMS pour générer le script de l’exécution du package, puis modifier le nom de la *runincluster* paramètre *runinscaleout* dans le script, exécutez le script.
-   Le catalogue SSIS a une nouvelle propriété globale afin de spécifier le mode par défaut pour l’exécution de packages SSIS. Cette nouvelle propriété s’applique lorsque vous appelez le **[catalogue]. [ create_execution]** procédure stockée avec la *runinscaleout* est défini sur null. Ce mode s’applique également aux travaux de l’Agent SQL de SSIS. Vous pouvez définir la propriété globale de nouveau dans la boîte de dialogue Propriétés du nœud SSISDB dans SSMS, ou avec la commande suivante :
    ```sql
    EXEC [catalog].[configure_catalog] @property_name=N'DEFAULT_EXECUTION_MODE', @property_value=1
    ```

## <a name="new-in-ssis-in-sql-server-2017-ctp-21"></a>Nouveau dans SSIS dans SQL Server CTP 2017 2.1

### <a name="new-and-changed-features-in-scale-out-for-ssis"></a>Fonctionnalités nouvelles et modifiées dans monter en charge de SSIS

-   Vous pouvez maintenant utiliser le **Use32BitRuntime** paramètre lorsque vous déclenchez l’exécution de monter en charge.
-   Les performances de journalisation pour SSISDB pour les exécutions de package dans monter en charge a été améliorée. Les journaux de Message d’événement et le contexte de Message sont désormais écrits sur SSISDB en mode batch au lieu d’un par un. Voici quelques remarques supplémentaires sur cette amélioration :        
    - Certains rapports dans la version actuelle de SQL Server Management Studio (SSMS) n’affichent pas actuellement ces journaux pour les exécutions de monter en charge. Nous estimons qu’elles sont prises en charge dans la prochaine version de SSMS. Rapports incluent le *toutes les connexions* rapport, le *contexte de l’erreur* rapport et le *les informations de connexion* section dans le tableau de bord de Service d’intégration.
    - Une nouvelle colonne **event_message_guid** a été ajouté. Utilisez cette colonne pour joindre le [catalogue]. affichage de [event_message_context] et [catalogue]. [event_messages] afficher au lieu d’utiliser **event_message_id** lorsque vous interrogez ces journaux des exécutions de monter en charge.
-   Pour obtenir de l’application de gestion pour SSIS monter en charge, [télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) 17.1 ou version ultérieure.

## <a name="new-in-ssis-in-sql-server-2017-ctp-20"></a>Nouveau dans SSIS dans SQL Server 2017 CTP 2.0

Il n’y a aucune nouvelle fonctionnalité SSIS dans SQL Server 2017 CTP 2.0.

## <a name="new-in-ssis-in-sql-server-2017-ctp-14"></a>Nouveau dans SSIS dans SQL Server 2017 CTP 1.4

Il n’y a aucune nouvelle fonctionnalité SSIS dans SQL Server 2017 CTP 1.4.

## <a name="new-in-ssis-in-sql-server-2017-ctp-13"></a>Nouveau dans SSIS dans SQL Server CTP 2017 1.3

Il n’y a aucune nouvelle fonctionnalité SSIS dans SQL Server 2017 CTP 1.3.

## <a name="new-in-ssis-in-sql-server-2017-ctp-12"></a>Nouveau dans SSIS dans SQL Server CTP 2017 1.2

Il n’y a aucune nouvelle fonctionnalité SSIS dans SQL Server 2017 CTP 1.2.

## <a name="new-in-ssis-in-sql-server-2017-ctp-11"></a>Nouveau dans SSIS dans SQL Server CTP 2017 1.1

Il n’y a aucune nouvelle fonctionnalité SSIS dans SQL Server 2017 CTP 1.1.

## <a name="new-in-ssis-in-sql-server-2017-ctp-10"></a>Nouveau dans SSIS dans SQL Server 2017 CTP 1.0

### <a name="scale-out-for-ssis"></a>Scale Out pour SSIS

La fonctionnalité Scale Out facilite grandement l’exécution de [!INCLUDE[ssIS_md](../includes/ssis-md.md)] sur plusieurs ordinateurs. 
   
Après l’installation du Scale Out Master et des Scale Out Workers, le package peut être distribué pour s’exécuter automatiquement sur différents Workers. Si l’exécution est arrêtée inopinément, une nouvelle tentative est effectuée automatiquement. De plus, vous pouvez gérer toutes les exécutions et Workers de manière centralisée à l’aide du Master.
   
Pour plus d’informations, consultez [Integration Services Scale Out](../integration-services/scale-out/integration-services-ssis-scale-out.md).
   
### <a name="support-for-microsoft-dynamics-online-resources"></a>Prise en charge des ressources Microsoft Dynamics Online

Le Gestionnaire de connexions OData et de sources OData prennent désormais en charge la connexion aux flux OData de Microsoft Dynamics AX Online et Microsoft Dynamics CRM Online.


