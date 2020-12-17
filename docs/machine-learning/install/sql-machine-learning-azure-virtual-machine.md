---
title: Installation sur une machine virtuelle Azure
description: Exécutez des solutions de science des données et de Machine Learning Python et R avec SQL Server Machine Learning Services sur une machine virtuelle dans le cloud Azure.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 01/02/2020
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15'
ms.openlocfilehash: e8eb32776aa72095c03305d4eb31cf5bb220ebe4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471240"
---
# <a name="install-sql-server-machine-learning-services-with-python-and-r-on-an-azure-virtual-machine"></a>Installation de SQL Server Machine Learning Services sur une machine virtuelle Azure avec Python et R
[!INCLUDE [SQL Server 2017 and later](../../includes/applies-to-version/sqlserver2017.md)]

Découvrez comment installer Python et R avec SQL Server Machine Learning Services sur une machine virtuelle dans Azure. Cela élimine les tâches d’installation et de configuration de Machine Learning Services.

Procédez comme suit :

1. Approvisionnement d’une machine virtuelle SQL Server dans Azure
1. Désactiver une règle du pare-feu
1. Autoriser les rappels ODBC pour les clients distants
1. Ajouter des protocoles réseau

## <a name="provision-sql-server-virtual-machine-in-azure"></a>Approvisionnement d’une machine virtuelle SQL Server dans Azure

Pour obtenir des instructions pas à pas, consultez [Provisionnement d’une machine virtuelle Windows SQL Server dans le Portail Azure](/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision). 

L’étape [Configurer les paramètres SQL Server](/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#3-configure-sql-server-settings) est le moment où vous ajoutez Machine Learning Services à votre instance.

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