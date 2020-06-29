---
title: Journalisation d’Integration Services (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], logs
- Windows Event log provider [Integration Services]
- XML File log provider [Integration Services]
- SQL Server Profiler, log provider
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- tasks [Integration Services], logs
- logs [Integration Services], log providers
- Integration Services packages, logs
- log providers [Integration Services]
- packages [Integration Services], logs
- Text File log provider
- SQL Server log provider
ms.assetid: 65e17889-371f-4951-9a7e-9932b2d0dcde
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 30f65b7bfd4563bbc9ada1d615f0d48af225895d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423406"
---
# <a name="integration-services-ssis-logging"></a>Journalisation d'Integration Services (SSIS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contient des modules fournisseur d'informations que vous pouvez utiliser pour implémenter la journalisation dans les packages, les conteneurs et les tâches. Avec la journalisation, vous pouvez capturer des informations d'exécution sur un package qui vous aideront à auditer et à résoudre les problèmes d'un package à chaque exécution. Un journal peut ainsi capturer le nom de l'opérateur ayant exécuté le package et l'heure à laquelle le package a débuté et s'est terminé.  
  
 Vous pouvez configurer l'étendue des informations enregistrées lors d'une exécution de package sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Pour plus d’informations, consultez [Activer la journalisation des exécutions de package sur le serveur SSIS](../enable-logging-for-package-execution-on-the-ssis-server.md).  
  
 Vous pouvez également inclure la journalisation lorsque vous exécutez un package à l'aide de l'utilitaire d'invite de commandes **dtexec** . Pour plus d'informations sur les arguments d'invite de commandes prenant en charge la journalisation, consultez [dtexec Utility](../packages/dtexec-utility.md).  
  
## <a name="configure-logging-in-sql-server-data-tools"></a>Configurer la journalisation dans les Outils de données SQL Server  
 Les journaux sont associés aux packages et configurés au niveau du package. Chaque tâche ou conteneur dans un package peut journaliser des informations dans n'importe quel journal de package. Les tâches et conteneurs d'un package peuvent être activés pour la journalisation même si le package lui-même ne l'est pas. Par exemple, vous pouvez activer la journalisation sur une tâche d'exécution SQL sans activer la journalisation sur le package parent. Un package, un conteneur ou une tâche peuvent écrire dans plusieurs journaux. Vous pouvez activer la journalisation sur le package uniquement, ou choisir d'activer la journalisation sur une tâche ou un conteneur individuel contenu dans le package.  
  
 Lorsque vous ajoutez le journal à un package, vous choisissez le module fournisseur d'informations et l'emplacement du journal. Le module fournisseur d'informations spécifie le format des données du journal, par exemple, une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou un fichier texte.  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] comprend les modules fournisseurs d'informations suivants :  
  
-   Le module fournisseur d'informations pour les fichiers texte, qui enregistre les entrées du journal dans des fichiers texte ASCII au format CSV. L'extension de nom de fichier par défaut de ce fournisseur est .log.  
  
-   Le module fournisseur d'informations pour le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] , qui enregistre des traces que vous pouvez ensuite afficher à l'aide de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler. L'extension de nom de fichier par défaut de ce fournisseur est .trc.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas utiliser le module fournisseur d’informations [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] dans un package exécuté en mode 64 bits.  
  
-   Module [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur d’informations qui écrit des entrées de journal dans la `sysssislog` table d’une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.  
  
-   Le module fournisseur d'informations pour les événements Windows, qui enregistre les entrées du journal des applications dans le journal des événements Windows sur l'ordinateur local.  
  
-   Le module fournisseur d'informations pour les fichiers XML, qui enregistre les fichiers journaux dans un fichier XML. L'extension de nom de fichier par défaut de ce fournisseur est .xml.  
  
 Si vous ajoutez un module fournisseur d'informations à un package ou configurez la journalisation par programmation, vous pouvez utiliser un ProgID ou un ClassID pour identifier ce module, au lieu d'utiliser les noms affichés par le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] dans la boîte de dialogue **Configurer les journaux SSIS** .  
  
 Le tableau suivant énumère les ProgID et ClassID des modules fournisseurs d'informations inclus dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , ainsi que l'emplacement des journaux dans lesquels les modules fournisseurs d'informations écrivent.  
  
|Module fournisseur d'informations|ProgID|ClassID|Location|  
|------------------|------------|-------------|--------------|  
|Fichier texte|DTS.LogProviderTextFile|{0A039101-ACC1-4E06-943F-279948323883}|Le gestionnaire de connexions de fichiers utilisé par le module fournisseur d'informations spécifie le chemin d'accès du fichier texte.|  
|SQL Server Profiler|DTS.LogProviderSQLProfiler|{E93F6300-AE0C-4916-A7BF-A8D0CE12C77A}|Le gestionnaire de connexions de fichiers utilisé par le module fournisseur d'informations spécifie le chemin d'accès du fichier utilisé par [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].|  
|SQL Server|DTS.LogProviderSQLServer|{94150B25-6AEB-4C0D-996D-D37D1C4FDEDA}|Le gestionnaire de connexions OLE DB utilisé par le module fournisseur d’informations spécifie la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant la table sysssislog avec les entrées de journal.|  
|Journal des événements Windows|DTS.LogProviderEventLog|{071CC8EB-C343-4CFF-8D58-564B92FCA3CF}|Le journal des applications dans l'Observateur d'événements Windows contient les informations de journalisation de [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .|  
|Fichier XML|DTS.LogProviderXMLFile|{440945A4-2A22-4F19-B577-EAF5FDDC5F7A}|Le gestionnaire de connexions de fichiers utilisé par le module fournisseur d'informations spécifie le chemin d'accès du fichier XML.|  
  
 Vous pouvez également créer des modules fournisseurs d'informations personnalisés. Pour plus d’informations, consultez [Creating a Custom Log Provider](../extending-packages-custom-objects/log-provider/creating-a-custom-log-provider.md).  
  
 Les modules fournisseurs d'informations d'un package sont membres de la collection des modules fournisseurs d'informations du package. Si vous créez un package et implémentez la journalisation à l'aide du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vous pouvez afficher la liste des membres de la collection dans les dossiers **Module fournisseur d'informations** de l'onglet **Explorateur de package** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
 Un module fournisseur d'informations est configuré en indiquant le nom et la description du module et en spécifiant le gestionnaire de connexions qu'il utilise. Le module fournisseur d'informations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise un gestionnaire de connexions OLE DB. Le fichier texte, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]et les modules fournisseurs d'informations pour les fichiers XML utilisent tous des gestionnaires de connexions de fichiers. Le module fournisseur d'informations pour les événements Windows n'utilise pas de gestionnaire de connexions, car il écrit directement dans le journal des événements Windows. Pour plus d'informations, consultez [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md) et [File Connection Manager](../connection-manager/file-connection-manager.md).  
  
### <a name="logging-customization"></a>Personnalisation de la journalisation  
 Pour personnaliser la journalisation d'un événement ou d'un message personnalisé, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] fournit un schéma d'informations fréquemment journalisées à inclure dans les entrées de journal. Le schéma de journal [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] définit les informations que vous pouvez journaliser. Vous pouvez sélectionner les éléments à partir du schéma de journal pour chaque entrée de journal.  
  
 Un package et ses conteneurs et tâches ne doivent pas journaliser la même information, et les tâches au sein du même package ou conteneur peuvent journaliser des informations différentes. Par exemple, un package peut journaliser des informations d'opérateur lorsque le package démarre, une tâche peut journaliser la source de l'échec de la tâche et une autre tâche peut journaliser les informations lorsque des erreurs surviennent. Si un package et ses conteneurs et tâches utilisent plusieurs journaux, les mêmes informations sont écrites dans tous les journaux.  
  
 Vous pouvez sélectionner un niveau de journalisation adapté à vos besoins en spécifiant les événements à journaliser et les informations à journaliser pour chaque événement. Vous pouvez estimer que certains événements fournissent des informations plus utiles que d'autres. Par exemple, vous pouvez ne journaliser que les noms d'ordinateur et d'opérateur pour l'événement **PreExecute** tout en journalisant toutes les informations disponibles pour l'événement **Error** .  
  
 Pour empêcher les fichiers journaux d'occuper de grands volumes sur l'espace disque ou pour éviter une journalisation excessive qui pourrait nuire aux performances, vous pouvez limiter la journalisation en sélectionnant des informations et événements spécifiques à journaliser. Par exemple, vous pouvez configurer un journal pour qu'il ne capture que la date et le nom de l'ordinateur pour chaque erreur.  
  
 Dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , vous pouvez définir les options de journalisation en utilisant la boîte de dialogue **Configurer les journaux SSIS** .  
  
#### <a name="log-schema"></a>Schéma de journal  
 Le tableau suivant décrit les éléments du schéma de journal.  
  
|Élément|Description|  
|-------------|-----------------|  
|Computer|Le nom de l'ordinateur sur lequel l'événement du journal est survenu.|  
|Opérateur|L'identité de l'utilisateur ayant lancé le package.|  
|SourceName|Le nom du conteneur ou de la tâche dans laquelle l'événement du journal est survenu.|  
|SourceID|L'identificateur unique du package ; la boucle Foreach, la boucle For ou le conteneur de séquences ; ou la tâche dans laquelle l'événement du journal est survenu.|  
|ExecutionID|L'identificateur global unique (GUID) de l'instance d'exécution du package.<br /><br /> Remarque : l’exécution d’un package unique peut créer des entrées de journal avec des valeurs différentes pour l’élément ExecutionID. Par exemple, lorsque vous exécutez un package dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], la phase de validation peut créer des entrées de journal avec un élément ExecutionID correspondant à [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Toutefois, la phase d'exécution peut créer des entrées de journal avec un élément ExecutionID correspondant à dtshost.exe. Autre exemple : lorsque vous exécutez un package qui contient des tâches d'exécution de package, chacune de ces tâches exécute un package enfant. Ces packages enfants peuvent créer des entrées de journal comportant un élément ExecutionID différent de celui des entrées de journal créées par le package parent.|  
|MessageText|Un message associé à l'entrée de journal.|  
|DataBytes|Un tableau d'octets spécifique à l'entrée du journal. La signification de ce champ varie en fonction de l'entrée du journal.|  
  
 Le tableau suivant décrit trois éléments supplémentaires du schéma de journal qui ne sont pas disponibles sous l'onglet **Détails** de la boîte de dialogue **Configurer les journaux SSIS** .  
  
|Élément|Description|  
|-------------|-----------------|  
|StartTime|Heure à laquelle le conteneur ou la tâche commence à s'exécuter.|  
|EndTime|Heure à laquelle le conteneur ou la tâche arrête de s'exécuter.|  
|DataCode|Valeur entière facultative qui contient généralement une valeur de l’énumération <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> qui indique le résultat de l’exécution du conteneur ou de la tâche :<br /><br /> 0 - Succès<br /><br /> 1 - Échec<br /><br /> 2 - Terminée<br /><br /> 3 - Annulée|  
  
##### <a name="log-entries"></a>Entrées du journal  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] prend en charge les entrées de journal sur des événements prédéfinis et fournit des entrées de journal personnalisées pour de nombreux objets [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . La boîte de dialogue **Configurer les journaux SSIS** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] répertorie ces événements et ces entrées de journal personnalisées.  
  
 Le tableau suivant décrit les événements prédéfinis qui peuvent être activés pour écrire des entrées de journal lorsque des événements générés à l'exécution surviennent. Ces entrées de journal s'appliquent aux exécutables, au package et aux conteneurs et tâches inclus dans le package. Le nom de l'entrée de journal est le même que l'événement généré à l'exécution et qui a provoqué l'écriture de l'entrée de journal.  
  
|Événements|Description|  
|------------|-----------------|  
|**OnError**|Écrit une entrée de journal lorsqu'une erreur se produit.|  
|**OnExecStatusChanged**|Écrit une entrée de journal lorsqu'une tâche (et non un conteneur) est interrompue ou reprise pendant le débogage.|  
|**OnInformation**|Écrit une entrée de journal pendant la validation et l'exécution d'un exécutable pour rapporter des informations.|  
|**OnPostExecute**|Écrit une entrée de journal immédiatement après la fin de l'exécution de l'exécutable.|  
|**OnPostValidate**|Écrit une entrée de journal lorsque la validation de l'exécutable est terminée.|  
|**OnPreExecute**|Écrit une entrée de journal immédiatement avant le début de l'exécution de l'exécutable.|  
|**OnPreValidate**|Écrit une entrée de journal lorsque la validation de l'exécutable débute.|  
|**OnProgress**|Écrit une entrée de journal lorsqu'une progression quantifiable a été réalisée par l'exécutable.|  
|**OnQueryCancel**|Écrit une entrée de journal pour chaque point de jonction dans le traitement de la tâche où il est possible d'annuler l'exécution.|  
|**OnTaskFailed**|Écrit une entrée de journal lorsqu'une tâche échoue.|  
|**OnVariableValueChanged**|Écrit une entrée de journal lorsque la valeur d'une variable est modifiée.|  
|**OnWarning**|Écrit une entrée de journal lorsqu'un avertissement survient.|  
|**PipelineComponentTime**|Pour chaque composant de flux de données, écrit une entrée de journal pour chaque phase de validation et d'exécution. L'entrée de journal spécifie le temps de traitement de chaque phase.|  
|**Diagnostic**|Écrit une entrée de journal qui fournit des informations de diagnostic.<br /><br /> Par exemple, vous pouvez enregistrer un message avant et après chaque appel à un fournisseur de données externes. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../troubleshooting/troubleshooting-tools-for-package-execution.md).|  
  
 Le package ainsi que de nombreuses tâches contiennent des entrées du journal personnalisées qui peuvent être activées pour la journalisation. Par exemple, la tâche d’envoi de courrier fournit l’entrée de journal personnalisée **SendMailTaskBegin** , qui journalise les informations quand l’exécution de la tâche démarre, mais avant d’envoyer un message électronique. Pour plus d’informations, consultez [messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
### <a name="differentiating-package-copies"></a>Différentiation entre des copies de packages  
 Les données de journalisation incluent le nom et le GUID du package auxquels les entrées de journal appartiennent. Si vous créez un package par copie d'un package existant, le nom et le GUID du package existant sont également copiés. Il est donc possible que deux packages aient le même nom et le même GUID, ce qui les rend difficiles à distinguer dans les données du journal.  
  
 Pour lever l'ambiguïté, vous devez mettre à jour le nom et le GUID des nouveaux packages. Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], vous pouvez régénérer le GUID dans la propriété `ID` et mettre à jour la valeur de la propriété `Name` dans la fenêtre Propriétés. Vous pouvez également modifier le GUID et le nom par programmation ou en utilisant l'invite de commandes **dtutil** . Pour plus d’informations, consultez [Définir les propriétés d’un package](../set-package-properties.md) et [Utilitaire dtutil](../dtutil-utility.md).  
  
### <a name="parent-logging-options"></a>Options de journalisation des parents  
 Souvent, les options de journalisation des tâches et conteneurs de séquences et de boucles For ou Foreach correspondent à celle du package ou du conteneur parent. Dans ce cas, vous pouvez configurer ces éléments pour qu'ils héritent des options de journalisation de leur conteneur parent. Par exemple, dans un conteneur de boucles For qui contient une tâche d'exécution SQL, cette tâche peut utiliser les options de journalisation définies pour le conteneur de boucles For. Pour utiliser les options de journalisation des parents, définissez la propriété LoggingMode du conteneur avec la valeur **UseParentSetting**. Vous pouvez définir cette propriété dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ou via la boîte de dialogue **Configurer les journaux SSIS** dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
### <a name="logging-templates"></a>Modèles de journalisation  
 Dans la boîte de dialogue **Configurer les journaux SSIS** , vous pouvez également créer et enregistrer comme modèles les configurations de journalisation fréquemment utilisées, puis utiliser ces modèles dans différents packages. Cette procédure facilite l'application d'une stratégie de journalisation cohérente à différents packages et la modification des paramètres de journaux par la mise à jour et l'application des modèles. Les modèles sont stockés sous forme de fichiers XML.  
  
 **Pour configurer la journalisation à l'aide de la boîte de dialogue Configurer les journaux SSIS**  
  
1.  Activez le package et ses tâches pour la journalisation. La journalisation peut s'effectuer au niveau du package, du conteneur et de la tâche. Vous pouvez spécifier différents journaux pour les packages, conteneurs et tâches.  
  
2.  Sélectionnez un module fournisseur d'informations et ajoutez un journal pour le package. Les journaux ne peuvent être créés qu'au niveau du package, et une tâche ou un conteneur doit utiliser un des journaux créés pour le package. Chaque journal est associé à l'un des modules fournisseurs d'informations suivants : fichier texte, [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], journal des événements Windows ou fichier XML. Pour plus d’informations, consultez [Activer la journalisation des packages dans les outils de données SQL Server](../enable-package-logging-in-sql-server-data-tools.md).  
  
3.  Sélectionnez les événements et les informations de schéma de journal pour chaque événement que vous voulez capturer dans le journal. Pour plus d’informations, consultez [Configurer la journalisation à l’aide d’un fichier de configuration enregistré](../configure-logging-by-using-a-saved-configuration-file.md).  
  
### <a name="configuration-of-log-provider"></a>Configuration du module fournisseur d'informations  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Un module fournisseur d'informations est créé et configuré dans le cadre de l'implémentation d'un package. Pour plus d’informations, consultez [Integration Services Logging](integration-services-ssis-logging.md).  
  
 Après avoir créé un module fournisseur d'informations, vous pouvez l'afficher et modifier ses propriétés dans la fenêtre Propriétés de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].  
  
 Pour plus d’informations sur la définition par programmation de ces propriétés, consultez la documentation relative à la classe <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> .  
  
### <a name="logging-for-data-flow-tasks"></a>Journalisation des tâches de flux de données  
 La tâche de flux de données fournit un grand nombre d'entrées de journal personnalisées à l'aide desquelles vous pouvez analyser et améliorer les performances. Vous pouvez, par exemple, analyser les composants susceptibles de provoquer des fuites de mémoire ou contrôler le temps nécessaire à l'exécution d'une tâche en particulier. Pour obtenir une liste de ces entrées de journal personnalisées et un exemple de sortie de journalisation, consultez [Data Flow Task](../control-flow/data-flow-task.md).  
  
#### <a name="use-the-pipelinecomponenttime-event"></a>Utiliser l'événement PipelineComponentTime  
 L'entrée de journal personnalisée la plus utile est peut-être l'événement PipelineComponentTime. Cette entrée de journal signale le nombre de millisecondes que chaque composant dans le flux de données passe sur chacune des cinq étapes de traitement majeures. Le tableau suivant décrit ces étapes de traitement. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Les développeurs reconnaîtront ces étapes comme étant les méthodes principales d’un <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>.  
  
|Étape|Description|  
|----------|-----------------|  
|Valider|Le composant recherche des valeurs de propriété et des paramètres de configuration valides.|  
|PreExecute|Le composant effectue un traitement unique avant de commencer à traiter les lignes de données.|  
|PostExecute|Le composant effectue un traitement unique après avoir traité toutes les lignes de données.|  
|ProcessInput|Le composant de transformation ou de destination traite les lignes de données entrantes qu'une source ou une transformation en amont lui a passées.|  
|PrimeOutput|Le composant source ou de transformation remplit les tampons de données à passer à un composant de transformation ou de destination en aval.|  
  
 Lorsque vous activez l'événement PipelineComponentTime, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] consigne un message pour chaque étape de traitement effectuée par chaque composant. Les entrées de journal suivantes illustrent un sous-ensemble des messages consignés par l'exemple de package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] CalculatedColumns :  
  
 `The component "Calculate LineItemTotalCost" (3522) spent 356 milliseconds in ProcessInput.`  
  
 `The component "Sum Quantity and LineItemTotalCost" (3619) spent 79 milliseconds in ProcessInput.`  
  
 `The component "Calculate Average Cost" (3662) spent 16 milliseconds in ProcessInput.`  
  
 `The component "Sort by ProductID" (3717) spent 125 milliseconds in ProcessInput.`  
  
 `The component "Load Data" (3773) spent 0 milliseconds in ProcessInput.`  
  
 `The component "Extract Data" (3869) spent 688 milliseconds in PrimeOutput filling buffers on output "OLE DB Source Output" (3879).`  
  
 `The component "Sum Quantity and LineItemTotalCost" (3619) spent 141 milliseconds in PrimeOutput filling buffers on output "Aggregate Output 1" (3621).`  
  
 `The component "Sort by ProductID" (3717) spent 16 milliseconds in PrimeOutput filling buffers on output "Sort Output" (3719).`  
  
 Ces entrées de journal montrent que la tâche de flux de données a passé la plupart du temps dans les étapes suivantes, répertoriées ici dans l'ordre décroissant :  
  
-   La source OLE DB nommée « Extract Data » a passé 688 ms à charger des données.  
  
-   La transformation de la colonne dérivée nommée « Calculate LineItemTotalCost » a passé 356 ms à exécuter des calculs sur les lignes entrantes.  
  
-   La transformation d’agrégation nommée « Sum Quantity and LineItemTotalCost » a passé un total de 220 ms (141 ms dans PrimeOutput et 79 ms dans ProcessInput) à effectuer des calculs et à passer les données à la transformation suivante.  
  
## <a name="related-tasks"></a>Tâches associées  
 La liste suivante contient des liens vers les rubriques qui indiquent comment effectuer les tâches relatives à la fonctionnalité de journalisation.  
  
-   [Configurer les journaux SSIS (boîte de dialogue)](../configure-ssis-logs-dialog-box.md)  
  
-   [Activer la journalisation des packages dans les outils de données SQL Server](../enable-package-logging-in-sql-server-data-tools.md)  
  
-   [Activer la journalisation des exécutions de package sur le serveur SSIS](../enable-logging-for-package-execution-on-the-ssis-server.md)  
  
-   [Afficher les entrées de journal dans la fenêtre Journaux d’événements](../view-log-entries-in-the-log-events-window.md)  
  
## <a name="related-content"></a>Contenu associé  
 [Outil DTLoggedExec pour un enregistrement complet et détaillé (projet CodePlex)](https://go.microsoft.com/fwlink/?LinkId=150579)  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher les entrées de journal dans la fenêtre Journaux d’événements](../view-log-entries-in-the-log-events-window.md)  
  
  
