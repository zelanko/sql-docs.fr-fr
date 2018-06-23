---
title: MSSQL_ENG014114 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014114 error
ms.assetid: f5f04590-e1c6-40d8-ab2b-98c791a0fc44
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 8560be4d90999f90bc76650842fca66596414683
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051918"
---
# <a name="mssqleng014114"></a>MSSQL_ENG014114
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14114|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|'%1!' n'est pas configuré en tant que distributeur.|  
  
## <a name="explanation"></a>Explication  
 Si le message d'erreur spécifie une instance particulière autre que 'null', l'instance spécifiée n'a pas été correctement configurée pour être reconnue comme serveur de distribution.  
  
 Si le message spécifie 'null' comme serveur de distribution, il n'y a pas d'entrée pour le serveur local dans la base de données **master** , ou bien l'entrée est incorrecte (peut-être parce que l'ordinateur a été renommé). La réplication requiert que tous les serveurs d'une topologie soient enregistrés avec le nom d'ordinateur et un nom d'instance facultatif (dans le cas d'une instance cluster, le nom du serveur virtuel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avec le nom d'instance facultatif). Pour que la réplication fonctionne correctement, la valeur renvoyée par `SELECT @@SERVERNAME` pour chaque serveur de la topologie doit correspondre au nom d'ordinateur ou au nom de serveur virtuel avec le nom d'instance facultatif.  
  
 La réplication n'est pas prise en charge si vous avez inscrit une des instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] par adresse IP ou par nom de domaine pleinement qualifié (FQDN). Si vous aviez une des instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] inscrites par adresse IP ou par nom de domaine pleinement qualifié dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] quand vous avez configuré la réplication, cette erreur a pu se produire.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si le message d'erreur spécifie une instance particulière, configurez le serveur comme serveur de distribution. Pour plus d’informations, consultez [Configurer la distribution](configure-distribution.md).  
  
 Si le message d'erreur ne spécifie pas d'instance particulière ('null'), vérifiez que l'instance du serveur de distribution est inscrit correctement. Si le nom réseau de l'ordinateur et le nom de l'instance SQL Server diffèrent, effectuez une des actions suivantes :  
  
-   Ajoutez le nom de l'instance SQL Server comme nom réseau valide. Pour définir un autre nom réseau, une méthode possible consiste à l'ajouter au fichier hosts local. Le fichier hosts local est installé par défaut dans le répertoire WINDOWS\system32\drivers\etc ou WINNT\system32\drivers\etc. Pour plus d'informations, consultez la documentation Windows.  
  
     Si, par exemple, le nom d'ordinateur est comp1, l'adresse IP de l'ordinateur 10.193.17.129 et le nom de l'instance inst1/nominst, ajoutez l'entrée suivante au fichier des hôtes :  
  
     10.193.17.129 inst1  
  
-   Désactivez la distribution, inscrivez l'instance puis réactivez la distribution. Si la valeur de @@SERVERNAME n’est pas correcte pour une instance non cluster, procédez comme suit :  
  
    ```  
    sp_dropserver '<old_name>', 'droplogins'  
    go  
    sp_addserver '<new_name>', 'local'  
    go  
    ```  
  
     Après avoir exécuté la procédure stockée [sp_addserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), vous devez redémarrer le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour que la modification apportée à @@SERVERNAME soit prise en compte.  
  
     Si la valeur de @@SERVERNAME n’est pas correcte pour une instance cluster, vous devez changer le nom à l’aide de l’administrateur de cluster. Pour plus d’informations, consultez [ Instances de Cluster de basculement AlwaysOn (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
