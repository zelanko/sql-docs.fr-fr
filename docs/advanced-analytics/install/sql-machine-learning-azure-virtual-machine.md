---
title: Installation sur une machine virtuelle Azure
description: Exécutez les solutions de science des données R et Python et de Machine Learning sur une machine virtuelle SQL Server dans le Cloud Azure.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: aeec25b561822e8083b89e03f0f7e74f40660f7b
ms.sourcegitcommit: 09ccd103bcad7312ef7c2471d50efd85615b59e8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73727614"
---
# <a name="install-sql-server-machine-learning-services-with-r-and-python-on-an-azure-virtual-machine"></a>Installation de SQL Server Machine Learning Services sur une machine virtuelle Azure avec R et Python
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Vous pouvez installer l’intégration R et Python avec Machine Learning Services sur une machine virtuelle SQL Server dans Azure, en éliminant les tâches d’installation et de configuration. Une fois la machine virtuelle déployée, les fonctionnalités sont prêtes à l’emploi.
 
Pour obtenir des instructions pas à pas, consultez [Provisionnement d’une machine virtuelle Windows SQL Server dans le Portail Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision).

L’étape [Configurer les paramètres SQL Server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#3-configure-sql-server-settings) est le moment où vous ajoutez Machine Learning à votre instance.

<a name="firewall"></a>

## <a name="unblock-the-firewall"></a>Désactiver une règle du pare-feu

Par défaut, le pare-feu de la machine virtuelle Azure comprend une règle qui bloque l’accès réseau pour les comptes d’utilisateur locaux.

Vous devez désactiver cette règle pour permettre l’accès à l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d’un client de science des données distant.  Sinon, votre code de Machine Learning ne peut pas s’exécuter dans des contextes de calcul utilisant l’espace de travail de la machine virtuelle.

Pour autoriser l’accès à partir des clients de science des données distants :

1. Sur la machine virtuelle, ouvrez le Pare-feu Windows avec fonctions avancées de sécurité.
2. Sélectionnez **Règles sortantes**.
3. Désactivez la règle suivante :
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
## <a name="enable-odbc-callbacks-for-remote-clients"></a>Autoriser les rappels ODBC pour les clients distants

Si vous pensez que les clients qui appellent le serveur auront besoin d’envoyer des requêtes ODBC dans leurs solutions de Machine Learning, vous devez vous assurer que Launchpad peut effectuer des appels ODBC pour le compte du client distant. 

Pour cela, vous devez autoriser les comptes de travail SQL utilisés par Launchpad à se connecter à l’instance. Pour plus d’informations, consultez [Créer un nom de connexion pour SQLRUserGroup](../security/create-a-login-for-sqlrusergroup.md).

<a name="network"></a>

## <a name="add-network-protocols"></a>Ajouter des protocoles réseau

+ Activer les canaux nommés
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] utilise le protocole des canaux nommés pour les connexions entre les ordinateurs client et serveur, ainsi que pour certaines connexions internes. Si ce protocole n’est pas activé, vous devez l’installer et l’activer sur la machine virtuelle Azure et sur tous les clients de science des données susceptibles de se connecter au serveur.
  
+ Activer TCP/IP

  Vous devez utiliser le protocole TCP/IP pour les connexions de bouclage. Si vous obtenez l’erreur « DBNETLIB, SQL Server n’existe pas ou n’est pas accessible », activez TCP/IP sur la machine virtuelle prenant en charge l’instance.