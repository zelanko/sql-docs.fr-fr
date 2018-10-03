---
title: Journal des traces du service Report Server | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- logs [Reporting Services], trace
- traces [Reporting Services]
- system information [Reporting Services]
- versions [Reporting Services]
ms.assetid: 2fde08b2-137d-4f4b-88e5-216030216e0d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2621f9a8e69cc27d5012e0c6a6f90946bec07dc5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161929"
---
# <a name="report-server-service-trace-log"></a>Report Server Service Trace Log
  Le [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] journal de trace de serveur de rapports est un fichier texte ASCII qui contient des informations détaillées pour les opérations de service de serveur de rapports, y compris celles effectuées par le Web de serveur de rapports de service, le Gestionnaire de rapports et le traitement en arrière-plan. Le fichier journal des traces comprend des informations redondantes qui sont consignées dans d'autres fichiers journaux, ainsi que des informations qui ne se trouvent nulle part ailleurs. Les informations du journal des traces sont utiles si vous déboguez une application qui comprend un serveur de rapports, ou si vous essayez de déterminer l'origine d'un problème consigné dans le journal des événements ou le journal des exécutions.  
  
> [!NOTE]  
>  Dans les versions antérieures, il existait plusieurs fichiers journaux des traces, un pour chaque application. Les fichiers suivants sont obsolètes et ne sont plus créés dans [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et versions ultérieures : ReportServerWebApp_*\<timestamp >*.log, ReportServer_*\<timestamp >*.log et ReportServerService_main_*\<timestamp >*. journal.  
  
 **Dans cette rubrique :**  
  
-   [Où se trouvent les fichiers journaux de serveur de rapports ?](#bkmk_view_log)  
  
-   [Paramètres de configuration de trace](#bkmk_trace_configuration_settings)  
  
-   [Ajout du paramètre de Configuration personnalisée pour spécifier un emplacement de fichier de vidage](#bkmk_add_custom)  
  
-   [Champs du fichier journal](#bkmk_log_file_fields)  
  
##  <a name="bkmk_view_log"></a> Où se trouvent les fichiers journaux de Report Server ?  
 Les fichiers journaux des traces sont `ReportServerService_<timestamp>.log` et se trouvent dans le dossier suivant :  
  
 `C:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles`  
  
 Le journal des traces est créé quotidiennement, à partir de la première entrée ayant lieu après minuit (heure locale), et chaque fois que le service redémarre. L'horodateur est basé sur l'heure UTC (Coordinated Universal Time). Le fichier est au format EN-US. Par défaut, les journaux des traces sont limités à 32 mégaoctets et par défaut, ils sont supprimés après 14 jours.  
  
 Visualiser une courte vidéo qui montre l'utilisation de Microsoft Power Query pour afficher des fichiers journaux [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] .  
  
 ![Regarder une vidéo sur les journaux SSRS et Power Query](../media/generic-video-thumbnail.png "regarder une vidéo sur les journaux SSRS et Power Query")  
  
##  <a name="bkmk_trace_configuration_settings"></a> Paramètres de configuration des traces  
 Le comportement du journal des traces est géré dans le fichier de configuration **ReportingServicesrService.exe.config**. Le fichier de configuration se trouve dans le chemin d'accès de dossier suivant :  
  
 `\Program Files\Microsoft SQL Server\MSRS12.<instance name>\Reporting Services\ReportServer\bin` .  
  
 L'exemple suivant illustre la structure XML des paramètres de `RStrace`. La valeur de `DefaultTraceSwitch` détermine le type d’information qui est ajouté au journal. À l’exception de la `Components` d’attribut, les valeurs de `RStrace` sont les mêmes pour les fichiers de configuration.  
  
```  
<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
```  
  
 Le tableau suivant fournit des informations sur chaque paramètre.  
  
|Paramètre|Description|  
|-------------|-----------------|  
|`RStrace`|Spécifie les espaces de noms utilisés pour les erreurs et la trace.|  
|`DefaultTraceSwitch`|Spécifie le niveau des informations consignées dans le journal de trace de ReportServerService. Chaque niveau comprend les informations signalées par tous les niveaux inférieurs. La désactivation de la trace n'est pas recommandée. Les valeurs valides sont :<br /><br /> 0 = Trace désactivée. Le fichier journal ReportServerService est activé par défaut. Pour le désactiver, définissez le niveau de trace à 0.<br /><br /> 1= Exceptions et redémarrages<br /><br /> 2= Exceptions, redémarrages, avertissements<br /><br /> 3= Exceptions, redémarrages, avertissements, messages d'état (par défaut)<br /><br /> 4= Mode commenté|  
|**FileName**|Spécifie la première partie du nom du fichier journal. La valeur spécifiée par `Prefix` complète le reste du nom.|  
|**FileSizeLimitMb**|Spécifie une taille maximale pour le journal de trace. La taille du fichier est exprimée en mégaoctets. Les valeurs valides vont de 0 à un entier maximal. La valeur par défaut est 32. Si vous spécifiez 0 ou un nombre négatif, le serveur de rapports considère que la valeur est égale à 1.<br /><br /> Vous pouvez surveiller la taille du fichier en définissant des niveaux de trace (de 0 à 4) pour contrôler la quantité de contenu enregistrée. Vous pouvez également spécifier les composants faisant l'objet d'une trace. Si la taille maximale du fichier journal est atteinte avant le délai d'expiration de 14 jours, les entrées les plus anciennes sont remplacées par les nouvelles entrées.|  
|**KeepFilesForDays**|Spécifie le nombre de jours après lequel supprimer un journal de trace. Les valeurs valides vont de 0 à un entier maximal. La valeur par défaut est 14. Si vous spécifiez 0 ou un nombre négatif, le serveur de rapports considère que la valeur est égale à 1.|  
|`Prefix`|Spécifie une valeur générée qui distingue une instance de journal d'une autre. Par défaut, des valeurs d'horodatage sont ajoutées aux noms des journaux de trace. Cette valeur est définie sur « tid, time ». Ne modifiez pas ce paramètre.|  
|**TraceListeners**|Spécifie une cible de sortie du contenu du journal de trace. Vous pouvez spécifier plusieurs cibles ; dans ce cas, utilisez la virgule comme séparateur. Les valeurs valides sont :<br /><br /> DebugWindow<br /><br /> File (par défaut)<br /><br /> StdOut|  
|**TraceFileMode**|Spécifie si les journaux de trace contiennent des données pour une période de 24 heures. Un seul journal de trace doit exister par composant et par jour. Cette valeur est définie sur « Unique » (par défaut). Ne modifiez pas cette valeur.|  
|`Components`|Spécifie les composants pour lesquels les informations du journal des traces sont générées, ainsi que le niveau des traces, dans le format suivant :<br /><br /> \<catégorie de composant>:\<tracelevel><br /><br /> Catégories de composants pouvant être définies :<br />Le composant `All` est utilisé pour effectuer le suivi de l'activité générale du serveur de rapports de tous les processus qui ne se retrouvent pas dans les catégories spécifiques.<br />`RunningJobs` est utilisé pour le suivi d’une opération de rapport ou abonnement en cours d’exécution.<br />Le composant `SemanticQueryEngine` est utilisé pour effectuer le suivi d'une requête sémantique qui est traitée lorsqu'un utilisateur effectue une exploration de données ad hoc dans un rapport basé sur un modèle.<br />Le composant `SemanticModelGenerator` est utilisé pour effectuer le suivi de la génération de modèle.<br />Le composant `http` sert à activer le fichier journal HTTP Report Server. Pour plus d’informations, consultez [journal HTTP Report Server](report-server-http-log.md).<br /><br /> <br /><br /> Valeurs valides pour le niveau de trace :<br /><br /> 0= Trace désactivée<br /><br /> 1= Exceptions et redémarrages<br /><br /> 2= Exceptions, redémarrages, avertissements<br /><br /> 3= Exceptions, redémarrages, avertissements, messages d'état (par défaut)<br /><br /> 4= Mode commenté<br /><br /> La valeur par défaut pour Report Server est : « all:3 ».<br /><br /> Vous pouvez spécifier tout ou partie des composants (`all`, `RunningJobs`, `SemanticQueryEngine`, `SemanticModelGenerator`). Si vous ne voulez pas générer les informations relatives à un composant spécifique, désactivez les traces de ce composant (par exemple, « SemanticModelGenerator:0 »). Ne désactivez pas les traces du composant `all`.<br /><br /> Si vous n'ajoutez pas de niveau de trace au composant, la valeur spécifiée pour `DefaultTraceSwitch` est utilisée. Par exemple, si vous spécifiez « all,RunningJobs,SemanticQueryEngine,SemanticModelGenerator », tous les composants utilisent le niveau des traces par défaut.<br /><br /> Vous pouvez définir « SemanticQueryEngine:4 » si vous voulez afficher les instructions Transact-SQL qui sont générées pour chaque requête sémantique. Les instructions Transact-SQL sont enregistrées dans le journal des traces. L'exemple suivant illustre le paramètre de configuration qui ajoute les instructions Transact-SQL au journal :<br /><br /> \<add name="Components" value="all,SemanticQueryEngine:4" />|  
  
##  <a name="bkmk_add_custom"></a> Ajout d'un paramètre de configuration personnalisé destiné à spécifier l'emplacement des fichiers de vidage  
 Vous pouvez ajouter un paramètre personnalisé visant à définir l'emplacement que Dr Watson pour Windows utilise pour stocker les fichiers de vidage. Ce paramètre personnalisé est `Directory`. L'exemple suivant illustre l'utilisation de ce paramètre de configuration dans la section `RStrace` :  
  
```  
<add name="Directory" value="U:\logs\" />  
```  
  
 Pour plus d'informations, consultez l' [article 913046 de la Base de connaissances](http://support.microsoft.com/?kbid=913046) sur le site Web de [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
##  <a name="bkmk_log_file_fields"></a> Champs du fichier journal  
 Un journal des traces contient les champs suivants :  
  
-   informations système, notamment le système d'exploitation, la version, le nombre de processeurs et la mémoire ;  
  
-   informations relatives à la version et au composant [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ;  
  
-   événements consignés dans le journal des applications ;  
  
-   exceptions générées par le serveur de rapports ;  
  
-   avertissements relatives aux ressources insuffisantes consignés par un serveur de rapports ;  
  
-   enveloppes SOAP entrantes et enveloppes SOAP sortantes résumées ;  
  
-   en-tête HTTP, trace de la pile et informations de suivi de débogage.  
  
 Vous pouvez consulter les informations du journal des traces pour déterminer si une remise de rapport s'est produite, qui a reçu le rapport et combien de tentatives de remises ont été effectuées. Les journaux de suivi enregistrent également l'activité d'exécution des rapports et les variables d'environnement qui sont en vigueur pendant le traitement des rapports. Les erreurs et les exceptions sont également consignées dans les journaux de suivi. Par exemple, vous pouvez trouver les rapports d’erreurs d’expiration (indiqué en tant qu’un `ThreadAbortExceptions` entrée).  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers journaux et sources de Reporting Services](../report-server/reporting-services-log-files-and-sources.md)   
 [Erreurs et événements référence &#40;Reporting Services&#41;](../troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  
