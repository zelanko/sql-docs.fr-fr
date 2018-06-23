---
title: Connexion à une base de données SQL Azure à l’aide de SQL Server Native Client | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 627854372a28762493b3c03b0ee17a8355789e09
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051948"
---
# <a name="connecting-to-a-azure-sql-database-using-sql-server-native-client"></a>Connexion à Azure SQL Database à l'aide de SQL Server Native Client
  Pour obtenir un exemple qui montre comment se connecter à un [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] à l’aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, consultez [développement : rubriques de procédures (base de données Windows Azure SQL)](http://msdn.microsoft.com/library/ee621787.aspx).  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>Problèmes connus lors de la connexion à une base de données SQL  
 Voici les problèmes connus liés à la connexion à une [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] à l'aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client :  
  
-   Une connexion établie avec `SQLBrowseConnect` peut être refusée si `SQLBrowseConnect` est utilisé au cours des étapes.  Supposons que le nom du pilote est transmis dans le premier appel, le serveur et les informations d'identification (utilisateur et mot de passe) sont envoyés dans le deuxième appel, établissant la connexion, et un nom de base de données et un langage sont envoyés dans le troisième appel.  Le troisième appel indique à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client d'émettre une instruction USE pour modifier les bases de données. Toutefois, l'instruction USE n'est pas prise en charge dans [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], ce qui génère l'erreur suivante :  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec SQL Server Native Client](building-applications-with-sql-server-native-client.md)  
  
  