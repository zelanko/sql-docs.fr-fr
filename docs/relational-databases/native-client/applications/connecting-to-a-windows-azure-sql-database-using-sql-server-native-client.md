---
title: Se connecter à Azure SQL DB
ms.custom: ''
ms.date: 03/14/2017
ms.reviewer: ''
ms.prod: sql
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 474db6d714d770ed5bfe0e509b79efc543ff1866
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81388200"
---
# <a name="connecting-to-an-azure-sql-database-using-sql-server-native-client"></a>Connexion à une base de données Azure SQL à l’aide de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Pour obtenir un exemple qui montre comment se connecter à [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l’aide de Native Client, consultez [développement : rubriques de procédures (Azure SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx).  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a>Problèmes connus lors de la connexion à une base de données SQL  
 Voici les problèmes connus liés à la connexion à une [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] à l'aide de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client :  
  
-   Une connexion établie avec **SQLBrowseConnect** peut être rejetée si **SQLBrowseConnect** est utilisé par étapes.  Supposons que le nom du pilote est transmis dans le premier appel, le serveur et les informations d'identification (utilisateur et mot de passe) sont envoyés dans le deuxième appel, établissant la connexion, et un nom de base de données et un langage sont envoyés dans le troisième appel.  Le troisième appel indique à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client d'émettre une instruction USE pour modifier les bases de données. Toutefois, l'instruction USE n'est pas prise en charge dans [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], ce qui génère l'erreur suivante :  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d'applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
