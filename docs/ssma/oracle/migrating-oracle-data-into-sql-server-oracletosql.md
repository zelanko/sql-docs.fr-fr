---
title: Migration de données Oracle dans SQL Server (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Oracle Data Migration, Client-Side Migration
- Oracle Data Migration,Server-Side Migration
ms.assetid: e23c5268-41ed-4e55-9fe7-a11376202a13
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: aacffa7cd65716969eae08488314eed08d4691e2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821207"
---
# <a name="migrating-oracle-data-into-sql-server-oracletosql"></a>Migration de données Oracle dans SQL Server (OracleToSQL)
Après avoir synchronisé correctement les objets convertis avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous pouvez migrer des données d’Oracle vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Si le moteur utilisé est le moteur de Migration de données côté serveur, puis, avant de pouvoir migrer des données, vous devez installer SSMA pour Oracle Extension Pack et les fournisseurs Oracle sur l’ordinateur qui est en cours d’exécution SSMA. Le service SQL Server Agent doit également être en cours d’exécution. Pour plus d’informations sur la façon d’installer le pack d’extension, consultez [installation des composants du serveur (OracleToSQL)](http://msdn.microsoft.com/33070e5f-4e39-4b70-ae81-b8af6e4983c5)  
  
## <a name="setting-migration-options"></a>Définition des Options de Migration  
Avant de migrer les données à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], passez en revue les options de migration de projet dans le **paramètres du projet** boîte de dialogue.  
  
-   À l’aide de cette boîte de dialogue vous pouvez définir des options telles que la taille de lot de migration, verrouillage de table, la vérification des contraintes, gestion des valeurs null et la gestion de valeur d’identité. Pour plus d’informations sur les paramètres de Migration de projet, consultez [paramètres du projet (Migration) (OracleToSQL)](http://msdn.microsoft.com/fcd6b988-633b-4b2b-9f36-6368b5e86b60).  
  
-   Le **moteur de Migration** dans le **paramètres du projet** boîte de dialogue permet à l’utilisateur effectuer le processus de migration à l’aide de deux types de moteurs de migration de données :  
  
    1.  Moteur de Migration de données côté client  
  
    2.  Moteur de Migration de données côté serveur  
  
**Migration des données côté client :**  
  
-   Pour lancer la migration des données côté client, sélectionnez le **moteur de Migration de données côté Client** option dans le **paramètres du projet** boîte de dialogue.  
  
-   Dans **paramètres du projet**, le **moteur de Migration de données côté Client** option est définie.  
  
    > [!NOTE]  
    > Le **moteur de Migration de données côté Client** réside à l’intérieur de l’application de SSMA et n’est, par conséquent, ne dépend pas la disponibilité du pack d’extension.  
  
**Migration des données côté serveur :**  
  
-   Pendant la migration des données côté serveur, le moteur se trouve sur la base de données cible. Il est installé par le pack d’extension. Pour plus d’informations sur la façon d’installer le pack d’extension, consultez [installation des composants serveur sur SQL Server](installing-ssma-components-on-sql-server-oracletosql.md)  
  
-   Pour lancer une migration sur le côté serveur, sélectionnez le **moteur de Migration de données côté serveur** option dans le **paramètres du projet** boîte de dialogue.  
  
## <a name="migrating-data-to-sql-server"></a>Migration de données vers SQL Server  
Migration de données sont une opération de chargement en masse qui déplace les lignes de données à partir des tables Oracle dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables dans des transactions. Le nombre de lignes chargées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans chaque transaction est configuré dans les paramètres du projet.  
  
Pour afficher les messages de la migration, assurez-vous que le volet de sortie est visible. Sinon, à partir de la **vue** menu, sélectionnez **sortie**.  
  
**Pour migrer des données**  
  
1.  Vérifiez les éléments suivants :  
  
    -   Les fournisseurs Oracle sont installés sur l’ordinateur qui est en cours d’exécution SSMA.  
  
    -   Vous avez synchronisé les objets convertis avec le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] base de données.  
  
2.  Dans l’Explorateur de métadonnées d’Oracle, sélectionnez les objets qui contiennent les données que vous souhaitez migrer :  
  
    -   Pour migrer des données pour tous les schémas, sélectionnez la case à cocher à côté **schémas**.  
  
    -   Pour migrer des données, ou omettre des tables individuelles, tout d’abord développer le schéma, développez **Tables**, puis sélectionnez ou désactivez la case à cocher en regard du tableau.  
  
3.  Pour migrer des données, deux arriver :  
  
    **Migration des données côté client :**  
  
    -   Pour effectuer des **Migration des données côté Client**, sélectionnez le **moteur de Migration de données côté Client** option dans le **paramètres du projet** boîte de dialogue.  
  
    **Migration des données côté serveur :**  
  
    -   Avant d’effectuer la migration des données côté serveur, vérifiez :  
  
        1.  SSMA pour Oracle Extension Pack est installé sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
        2.  Le service SQL Server Agent est en cours d’exécution sur l’instance de SQL Server.  
  
    -   Pour effectuer des **Migration des données côté serveur**, sélectionnez le **moteur de Migration de données côté serveur** option dans le **paramètres du projet** boîte de dialogue.  
  
4.  Avec le bouton droit **schémas** dans l’Explorateur de métadonnées d’Oracle, puis cliquez sur **migrer des données**. Vous pouvez également migrer des données pour des objets individuels ou des catégories d’objets : avec le bouton droit de l’objet ou son dossier parent ; Sélectionnez le **migrer des données** option.  
  
    > [!NOTE]  
    > Si l’Assistant SSMA pour Oracle Extension Pack n’est pas installé sur l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]et si **moteur de Migration de données côté serveur** est sélectionnée, puis lors de la migration des données à la base de données cible, l’erreur suivante survient : » Composants de la Migration des données SSMA sont introuvables sur SQL Server, migration de données côté serveur ne sera pas possible. Vérifiez si le Pack d’Extension est correctement installé ». Cliquez sur **Annuler** pour mettre fin à la migration des données.  
  
5.  Dans le **se connecter à Oracle** boîte de dialogue, entrez les informations d’identification de connexion, puis cliquez sur **Connect**. Pour plus d’informations sur la connexion à Oracle, consultez [se connecter à Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/connect-to-oracle-oracletosql.md)  
  
    Pour la connexion à la base de données cible [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], entrez les informations d’identification de connexion dans le **se connecter à SQL Server** boîte de dialogue, puis cliquez sur **Connect**. Pour plus d’informations sur la connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [se connecter à SQL Server](http://msdn.microsoft.com/bb8c4bde-cfc2-4636-92ae-5dd24abe9536)  
  
    Messages seront affichés dans le **sortie** volet. Une fois la migration terminée, le **rapport de Migration de données** s’affiche. Si aucune donnée n’a pas été migré, cliquez sur la ligne qui contient les erreurs, puis cliquez sur **détails**. Lorsque vous avez terminé avec le rapport, cliquez sur **fermer**. Pour plus d’informations sur le rapport de Migration de données, consultez [rapport de Migration de données (SSMA courant)](http://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241)  
  
> [!NOTE]  
> Lors de l’édition de SQL Express est utilisée en tant que la base de données cible, uniquement les migration de données côté client est autorisée et la migration des données côté serveur n’est pas pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
[Bases de données de migration d’Oracle vers SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
