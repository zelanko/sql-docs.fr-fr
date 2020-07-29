---
title: Se connecter à SQL Server ou Azure SQL Database
ms.custom: seo-lt-2019
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 9803a8a0-a8f1-4b65-87b8-989b06850194
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 9d489dac9355a573473063d1cafb32d42ed5fd98
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001991"
---
# <a name="connect-to-a-sql-server-or-azure-sql-database"></a>Se connecter à SQL Server ou Azure SQL Database

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Pour travailler avec des serveurs et des bases de données, vous devez d’abord vous connecter au serveur. Vous pouvez vous connecter à plusieurs serveurs en même temps.

[SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md) prend en charge plusieurs types de connexions. Cet article fournit des détails pour la connexion à SQL Server et à Azure SQL Database (connexion à un pool élastique ou une base de données unique Azure SQL). Pour plus d’informations sur les autres options de connexion, consultez les [liens](#see-also) au bas de cette page.
  
## <a name="connecting-to-a-server"></a>Connexion à un serveur  

1. Dans l’**Explorateur d’objets**, cliquez sur **Connexion > Moteur de base de données...** .

   ![se connecter](../media/connect-to-server/connect-db-engine.png)

1. Renseignez l’écran **Se connecter au serveur** et cliquez sur **Connexion** :

   ![connect to server](../media/connect-to-server/connect.png)

1. Si vous vous connectez à un serveur SQL Azure, vous serez peut-être invité à vous connecter pour créer une règle de pare-feu. Cliquez sur **Connexion...** (sinon, passez à l’étape 6 ci-dessous)

   ![pare-feu](../media/connect-to-server/firewall-rule-sign-in.png)

1. Une fois que vous êtes connecté, l’écran est prérempli avec votre adresse IP spécifique. Si votre adresse IP change souvent, il peut être plus simple d’accorder l’accès à une plage, donc sélectionnez l’option qui convient le mieux à votre environnement. 

   ![pare-feu](../media/connect-to-server/new-firewall-rule.png)

1. Pour créer la règle de pare-feu et vous connecter au serveur, cliquez sur **OK**.

1. Le serveur s’affiche dans l’**Explorateur d’objets** après vous être connecté :

   ![connected](../media/connect-to-server/connected.png)

## <a name="next-steps"></a>Étapes suivantes

[Concevoir, créer et mettre à jour des tables](../visual-db-tools/design-tables-visual-database-tools.md)

## <a name="see-also"></a>Voir aussi

[SQL Server Management Studio (SSMS)](../sql-server-management-studio-ssms.md)  
[Télécharger SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md)

[Analysis Services](https://docs.microsoft.com/sql/analysis-services/instances/connect-to-analysis-services)  
[Services d’intégration](https://docs.microsoft.com/sql/integration-services/sql-server-integration-services)  
[Reporting Services](https://docs.microsoft.com/sql/reporting-services/tools/connect-to-a-report-server-in-management-studio)  
[Stockage Azure](../f1-help/connect-to-microsoft-azure-storage.md)  
