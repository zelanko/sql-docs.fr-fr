---
title: Autres emplacements du dossier d’instantané | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 437553b0-19df-4522-8f27-06b5bc747c69
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c86e79928bdadb129ed0aa591e4bd035ffe22c1c
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54128999"
---
# <a name="alternate-snapshot-folder-locations"></a>Autres emplacements du dossier d'instantané
  Les autres emplacements d'instantané vous permettent de stocker les fichiers d'instantanés dans un lieu autre que l'emplacement par défaut (généralement, sur le serveur de distribution), ou s'ajoutent à cet emplacement par défaut. Il peut s'agir d'un autre serveur, d'un lecteur réseau ou d'un support amovible tel qu'un CD-ROM ou un disque.  
  
 L'autre emplacement d'instantané est mémorisé sous la forme d'une propriété de la publication. Dans la mesure où cet emplacement est une propriété de la publication, l'Agent de distribution et l'Agent de fusion sont capables de déterminer l'instantané approprié dans le cadre du processus de synchronisation.  
  
 Si vous souhaitez spécifier un autre emplacement pour le dossier d'instantanés ou compresser des fichiers d'instantanés, créez la publication sans créer immédiatement l'instantané initial, définissez les propriétés de publication de l'emplacement de l'instantané, puis exécutez l'Agent d'instantané pour cette publication. Si vous changez l'autre emplacement après avoir créé l'instantané initial, les instantanés déjà générés pour la publication ne seront pas transférés vers le nouvel emplacement. Dans ce cas, et en fonction des paramètres de publication, l'Agent de fusion ou de distribution ne trouvera peut-être pas les fichiers d'instantanés dans le nouvel emplacement.  
  
> [!NOTE]  
>  Ne spécifiez pas un autre emplacement (à l’aide de la boîte de dialogue **Propriétés de la publication** ou [sp_changepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)) qui soit identique à l’emplacement par défaut du dossier d’instantané.  
  
> [!CAUTION]  
>  N'utilisez pas WebSync et d'autres emplacements de dossier d'instantanés à la fois.  
  
 **Pour spécifier un autre emplacement d'instantané**  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Spécifiez un emplacement de dossier d’instantanés de remplacement](snapshot-options.md#snapshot-folder-locations) 
  
-   Programmation de la réplication [!INCLUDE[tsql](../../includes/tsql-md.md)] : [Configurer les propriétés d’instantané &#40;programmation Transact-SQL de la réplication&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement avec un instantané](initialize-a-subscription-with-a-snapshot.md)   
 [Options d’instantané](snapshot-options.md)  
  
  
