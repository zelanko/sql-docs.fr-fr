---
title: Utilisez SQL Server (XEvents) d’événements étendus pour surveiller Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b57cc2fe-52dc-4fa9-8554-5a866e25c6d7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6d6abfca98386ef691add200d433af827ed44836
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66079735"
---
# <a name="use-sql-server-extended-events-xevents-to-monitor-analysis-services"></a>Utiliser des événements étendus SQL Server (XEvents) pour surveiller Analysis Services
  Analysis Services fournit des fonctionnalités de suivi via l’utilisation de [événements étendus](../../relational-databases/extended-events/extended-events.md).  
  
 Les événements étendus constituent une infrastructure d'événements qui est très évolutive et configurable pour les systèmes serveur. Les événements étendus sont un système léger d'analyse des performances qui utilise très peu de ressources de performances.  
  
 Tous les événements peuvent être capturés de Analysis Services et la cible sur des consommateurs spécifiques, tels que définis dans [événements étendus](../../relational-databases/extended-events/extended-events.md), via XEvents.  
  
## <a name="initiating-extended-events-in-analysis-services"></a>Initialisation d'événements étendus dans Analysis Services  
 Le traçage d'événements étendus est activé à l'aide d'une commande de script de création d'objet XMLA semblable à celle ci-dessous :  
  
```  
<Execute ...>  
   <Command>  
      <Batch ...>  
         <Create ...>  
            <ObjectDefinition>  
               <Trace>  
                  <ID>trace_id</ID>  
                  <Name>trace_name</Name>  
                  <ddl300_300:XEvent>  
                     <event_session ...>  
                        <event package="AS" name="AS_event">  
                           <action package="PACKAGE0" .../>  
                        </event>  
                        <target package="PACKAGE0" name="asynchronous_file_target">  
                           <parameter name="filename" value="data_filename.xel"/>  
                           <parameter name="metadatafile" value="metadata_filename.xem"/>  
                        </target>  
                     </event_session>  
                  </ddl300_300:XEvent>  
               </Trace>  
            </ObjectDefinition>  
         </Create>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 Les éléments suivants seront définis par l'utilisateur, selon les besoins de suivi :  
  
 *trace_id*  
 Définit l'identificateur unique pour cette trace.  
  
 *trace_name*  
 Nom donné à cette trace ; habituellement une définition compréhensible de la trace. On utilise généralement la valeur *trace_id* comme nom.  
  
 *AS_event*  
 Événement Analysis Services à exposer. Consultez [Événements de trace Analysis Services](https://docs.microsoft.com/bi-reference/trace-events/analysis-services-trace-events) pour les noms des événements.  
  
 *data_filename*  
 Nom du fichier qui contient les données d'événement. Ce nom est suffixé avec un horodatage pour éviter que les données soient écrasées si la trace est envoyée plusieurs fois.  
  
 *metadata_filename*  
 Nom du fichier qui contient les métadonnées d'événement. Ce nom est suffixé avec un horodatage pour éviter que les données soient écrasées si la trace est envoyée plusieurs fois.  
  
## <a name="stopping-extended-events-in-analysis-services"></a>Arrêt des événements étendus dans Analysis Services  
 Pour arrêter les événements étendus qui tracent l'objet, vous devez supprimer cet objet à l'aide d'une commande de script de suppression d'objet XMLA semblable à celle ci-dessous :  
  
```  
<Execute xmlns="urn:schemas-microsoft-com:xml-analysis">  
   <Command>  
      <Batch ...>  
         <Delete ...>  
            <Object>  
               <TraceID>trace_id</TraceID>  
            </Object>  
         </Delete>  
      </Batch>  
   </Command>  
   <Properties></Properties>  
</Execute>  
  
```  
  
 Les éléments suivants seront définis par l'utilisateur, selon les besoins de suivi :  
  
 *trace_id*  
 Définit l'identificateur unique pour la trace à supprimer.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  
