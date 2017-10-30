---
title: "Se connecter à la base de données de catalogue SSISDB sur Azure | Documents Microsoft"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 560965a241b24a09f50a23faf63ce74d0049d5a7
ms.openlocfilehash: ac121e600c3c616006d79892c50f796ca7cd6b3f
ms.contentlocale: fr-fr
ms.lasthandoff: 10/13/2017

---
# <a name="connect-to-the-ssisdb-catalog-database-on-azure"></a>Se connecter à la base de données de catalogue SSISDB sur Azure

Obtenir les informations de connexion que vous souhaitez vous connecter à la base de données de catalogue SSISDB hébergée sur un serveur de base de données SQL Azure. Vous avez besoin des éléments suivants pour vous connecter :
- nom du serveur complet
- nom de la base de données
- informations de connexion 

## <a name="prerequisites"></a>Conditions préalables
Avant de commencer, assurez-vous que vous avez 17,2 ou version ultérieure de SQL Server Management Studio. Pour télécharger la dernière version de SSMS, consultez [télécharger SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="get-the-connection-info-from-the-azure-portal"></a>Obtenir les informations de connexion à partir du portail Azure
1. Connectez-vous au [portail Azure](https://portal.azure.com/).
2. Dans le portail Azure, sélectionnez **bases de données SQL** dans le menu de gauche, puis sélectionnez le `SSISDB` de la base de données sur le **bases de données SQL** page. 
3. Sur le **vue d’ensemble** page pour le `SSISDB` de base de données, passez en revue le nom du serveur complet, comme illustré dans l’image suivante. Placez le curseur sur le nom du serveur pour afficher le **copie** option.

    ![Informations de connexion de serveur](media/ssis-azure-connect-to-catalog-database/server-name.png) 

4. Si vous avez oublié les informations de connexion pour le serveur de base de données SQL, accédez à la page serveur de base de données SQL. Vous pouvez y consulter l’administrateur du serveur nom et, si nécessaire, réinitialiser le mot de passe.

## <a name="connect-with-ssms"></a>Connectez-vous à SSMS
1. Ouvrez SQL Server Management Studio.

2. **Connectez-vous au serveur**. Dans le **se connecter au serveur** boîte de dialogue, entrez les informations suivantes :

   | Paramètre       | Valeur suggérée |  Description | 
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **Type de serveur** | Moteur de base de données | Cette valeur est requise. |
   | **Nom du serveur** | Le nom du serveur complet | Le nom doit être au format suivant : **mysqldbserver.database.windows.net**. |
   | **Authentification** | Authentification SQL Server | Ce démarrage rapide utilise l’authentification SQL. |
   | **Connexion** | Le compte d’administrateur de serveur | Il s’agit du compte que vous avez spécifié lorsque vous avez créé le serveur. |
   | **Mot de passe** | Le mot de passe pour votre compte d’administrateur de serveur | Il s’agit du mot de passe que vous avez spécifié lorsque vous avez créé le serveur. |

3. **Se connecter à la base de données SSISDB**. Sélectionnez **Options** pour développer le **se connecter au serveur** boîte de dialogue. Dans l’étendue **se connecter au serveur** boîte de dialogue, sélectionnez le **propriétés de connexion** onglet. Dans le **se connecter à la base de données** champ, sélectionnez ou entrez `SSISDB`.

    > [!IMPORTANT]
    > Si vous ne sélectionnez pas `SSISDB` lorsque vous vous connectez, vous ne pouvez pas voir le catalogue SSIS dans l’Explorateur d’objets.

4. Puis sélectionnez **connexion**.

5. Dans l’Explorateur d’objets, développez **catalogues Integration Services** , puis **SSISDB** pour afficher les objets dans la base de données du catalogue SSIS.

## <a name="next-steps"></a>Étapes suivantes
- Déployer un package. Pour plus d’informations, consultez [déployer un projet SSIS avec SQL Server Management Studio (SSMS)](../ssis-quickstart-deploy-ssms.md).
- Exécuter un package. Pour plus d’informations, consultez [exécuter un package SSIS avec SQL Server Management Studio (SSMS)](../ssis-quickstart-run-ssms.md).
- Planifier un package. Pour plus d’informations, consultez [du package SSIS de la planification d’exécution sur Azure](ssis-azure-schedule-packages.md)

