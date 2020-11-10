---
description: Se connecter à SQL Server ou Azure SQL Database
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
ms.openlocfilehash: de873f30e435a1513e8e642cf5e3a97641e147d6
ms.sourcegitcommit: 80701484b8f404316d934ad2a85fd773e26ca30c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93243728"
---
# <a name="connect-to-a-sql-server-or-azure-sql-database"></a>Se connecter à SQL Server ou Azure SQL Database

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Pour travailler avec des serveurs et des bases de données, vous devez d’abord vous connecter au serveur. Vous pouvez vous connecter à plusieurs serveurs en même temps.

[SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md) prend en charge plusieurs types de connexions. Cet article fournit des détails pour la connexion à SQL Server et à Azure SQL Database (connexion à un pool élastique ou une base de données unique Azure SQL). Pour plus d’informations sur les autres options de connexion, consultez les [liens](#see-also) au bas de cette page.
  
## <a name="connecting-to-a-server"></a>Connexion à un serveur  

1. Dans l’ **Explorateur d’objets** , cliquez sur **Connexion > Moteur de base de données...**.

   ![se connecter](../media/connect-to-server/connect-db-engine.png)

1. Renseignez l’écran **Se connecter au serveur** et cliquez sur **Connexion**  :

   ![connect to server](../media/connect-to-server/connect.png)

1. Si vous vous connectez à un serveur SQL Azure, vous serez peut-être invité à vous connecter pour créer une règle de pare-feu. Cliquez sur **Connexion...** (sinon, passez à l’étape 6 ci-dessous)

   ![Capture d’écran de la boîte de dialogue Nouvelle règle de pare-feu, avec l’option Connexion mise en évidence.](../media/connect-to-server/firewall-rule-sign-in.png)

1. Une fois que vous êtes connecté, l’écran est prérempli avec votre adresse IP spécifique. Si votre adresse IP change souvent, il peut être plus simple d’accorder l’accès à une plage, donc sélectionnez l’option qui convient le mieux à votre environnement. 

   ![Capture d’écran de la boîte de dialogue Nouvelle règle de pare-feu, avec l’option Ajouter mon adresse IP cliente sélectionnée et l’option OK mise en évidence.](../media/connect-to-server/new-firewall-rule.png)

1. Pour créer la règle de pare-feu et vous connecter au serveur, cliquez sur **OK**.

1. Le serveur s’affiche dans l’ **Explorateur d’objets** après vous être connecté :

   ![Capture d’écran de l’Explorateur d’objets montrant que le serveur est correctement connecté.](../media/connect-to-server/connected.png)

## <a name="next-steps"></a>Étapes suivantes

[Concevoir, créer et mettre à jour des tables](../visual-db-tools/design-tables-visual-database-tools.md)

## <a name="see-also"></a>Voir aussi

[SQL Server Management Studio (SSMS)](../sql-server-management-studio-ssms.md)  
[Télécharger SQL Server Management Studio (SSMS)](../download-sql-server-management-studio-ssms.md)

[Analysis Services](/analysis-services/instances/connect-from-client-applications-analysis-services)  
[Services d’intégration](../../integration-services/sql-server-integration-services.md)  
[Reporting Services](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)  
[Stockage Azure](../f1-help/connect-to-microsoft-azure-storage.md)