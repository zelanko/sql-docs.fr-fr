---
title: Cible de fichier | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- event file target
- file target [SQL Server extended events]
- targets [SQL Server extended events], file target
ms.assetid: 4f0ee6ec-a0a8-4c38-aa61-8293ab6ac7fd
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4ea74f0361d5152ade31a91424d594d376e513f8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779452"
---
# <a name="event-file-target"></a>Event File Target
  La cible de fichier d'événements est une cible qui écrit des tampons complets sur le disque.  
  
 Le tableau ci-dessous décrit les options disponibles pour configurer la cible de fichier d'événements.  
  
|Option|Valeurs autorisées|Description|  
|------------|--------------------|-----------------|  
|filename|Toute chaîne incluant jusqu'à 260 caractères. Cette valeur est requise.|Emplacement et nom du fichier.<br /><br /> Vous pouvez utiliser toute extension de nom de fichier.|  
|max_file_size|Tout entier de 64 bits. Cette valeur est facultative.|Taille maximale du fichier, en mégaoctets (Mo). Si l'option max_file_size n'est pas spécifiée, la taille du fichier augmente jusqu'à ce que le disque soit saturé. La taille de fichier par défaut est 1 Go.<br /><br /> max_file_size doit être supérieure à la taille actuelle des tampons de session. Si ce n'est pas le cas, la cible de fichier ne pourra pas s'initialiser, et indiquera que max_file_size n'est pas valide. Pour afficher la taille actuelle des mémoires tampons, interrogez la colonne buffer_size dans la vue de gestion dynamique [sys.dm_xe_sessions](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql) .<br /><br /> Si la taille de fichier par défaut est plus petite que la taille de la mémoire tampon de session, nous vous recommandons d’affecter à max_file_size la valeur spécifiée dans la colonne max_memory dans l’affichage catalogue [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) .<br /><br /> Lorsque max_file_size a une taille plus grande que la taille des tampons de session, cette valeur peut être arrondie au multiple le plus proche de la taille de la mémoire tampon de session. Cela peut créer un fichier cible qui est plus petit que la valeur spécifiée de max_file_size. Par exemple, si la taille de la mémoire tampon est de 100 Mo et que max_file_size a la valeur 150 Mo, la taille de fichier résultante est arrondie à 100 Mo parce qu'une deuxième mémoire tampon ne tiendrait pas dans l'espace de 50 Mo restant.<br /><br /> Si la taille de fichier par défaut est plus petite que la taille de la mémoire tampon de session, nous vous recommandons d’affecter à max_file_size la valeur figurant dans la colonne max_memory dans l’affichage catalogue [sys.server_event_sessions](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql) .|  
|max_rollover_files|Tout entier de 32 bits. Cette valeur est facultative.|Nombre maximal de fichiers à conserver dans le système de fichiers. La valeur par défaut est 5.|  
|increment|Tout entier de 32 bits. Cette valeur est facultative.|Croissance incrémentielle, en mégaoctets (Mo), pour le fichier. Si cette option n'est pas spécifiée, la valeur par défaut pour l'incrément est égale à deux fois la taille de la mémoire tampon de session.|  
  
 La première fois qu’une cible de fichier d’événements est créée, le nom de fichier que vous spécifiez reçoit le suffixe _0\_ et une valeur d’entier long. La valeur entière est calculée en tant que le nombre de millisecondes écoulées entre le 1er janvier 1601 et la date et l’heure du fichier est créé. Les fichiers de substitution suivants utilisent également ce format. En examinant la valeur de l'entier long, vous pouvez déterminer le fichier le plus actuel. L'exemple suivant illustre comment les fichiers sont nommés dans un scénario où vous spécifiez l'option de nom de fichier comme C:\OutputFiles\MyOutput.xel :  
  
-   premier fichier créé - C:\OutputFiles\MyOutput_0_128500310259380000.xel  
  
-   premier fichier de substitution - C:\OutputFiles\MyOutput_0_128505831770890000.xel  
  
-   deuxième fichier de substitution - C:\OutputFiles\MyOutput_0_132410772966237000.xel  
  
## <a name="adding-the-target-to-a-session"></a>Ajout de la cible à une session  
 Pour ajouter la cible du fichier d’événements à une session Événements étendus, vous devez inclure les instructions suivantes quand vous créez ou modifiez une session d’événements, en remplaçant *file_name* par le nom de fichier et le chemin souhaités :  
  
```  
ADD TARGET package0.event_file(  
   SET filename='file_name.xel')  
```  
  
## <a name="reviewing-the-target-output"></a>Vérification de la sortie cible  
 Pour vérifier la sortie de la cible de fichier, vous devez utiliser la fonction sys.fn_xe_file_target_read_file. Nous vous recommandons de convertir les données au format XML. Vous pouvez utiliser la syntaxe suivante, en remplaçant *file_name* par le nom de fichier et le chemin que vous avez spécifiés quand vous avez ajouté la cible :  
  
```  
SELECT *, CAST(event_data AS XML) AS 'event_data_XML'  
FROM sys.fn_xe_file_target_read_file('file_name*.xel', NULL, NULL, NULL)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Cibles des Événements étendus SQL Server](../../2014/database-engine/sql-server-extended-events-targets.md)   
 [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)   
 [CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql)  
  
  
