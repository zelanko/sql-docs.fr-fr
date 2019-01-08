---
title: 'Langue de l’installation de R et des fonctionnalités de Python sur une machine virtuelle Azure : SQL Server Machine Learning Services'
description: Exécutez la science des données R et Python et des solutions sur une machine virtuelle de SQL Server dans le cloud Azure machine learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 6216142708a201a1ad720ab4e1e659c507744195
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432302"
---
# <a name="install-sql-server-machine-learning-services-with-r-and-python-on-an-azure-virtual-machine"></a>Installer les Services SQL Server Machine Learning avec R et Python sur une machine virtuelle Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Vous pouvez installer l’intégration de R et Python à Machine Learning Services sur une machine virtuelle de SQL Server dans Azure, en éliminant les tâches d’installation et la configuration. Une fois que l’ordinateur virtuel est déployé, les fonctionnalités sont prêtes à utiliser.
 
Pour obtenir des instructions étape par étape, consultez [comment approvisionner une machine virtuelle de Windows SQL Server dans le portail Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision).

Le [paramètres de configuration de SQL server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#4-configure-sql-server-settings) étape consiste où vous ajoutez apprentissage à votre instance.

<a name="firewall"></a>

## <a name="unblock-the-firewall"></a>Débloquer le pare-feu

Par défaut, le pare-feu sur la machine virtuelle Azure comprend une règle qui bloque accès pour les comptes d’utilisateurs locaux l'réseau.

Vous devez désactiver cette règle pour vous assurer que vous pouvez accéder à la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance à partir d’un client de science des données distantes.  Sinon, votre code d’apprentissage ne peut pas exécuter dans des contextes de calcul qui utilisent l’espace de travail de la machine virtuelle.

Pour activer l’accès à partir de clients de science des données à distance :

1. Sur la machine virtuelle, ouvrez le Pare-feu Windows avec fonctions avancées de sécurité.
2. Sélectionnez **Règles sortantes**.
3. Désactivez la règle suivante :
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
## <a name="enable-odbc-callbacks-for-remote-clients"></a>Autoriser les rappels ODBC pour les clients distants

Si vous prévoyez que les clients qui appellent le serveur devrez envoyer des requêtes ODBC dans le cadre de leurs solutions d’apprentissage, vous devez vous assurer que Launchpad peut effectuer des appels ODBC pour le compte du client distant. 

Pour cela, vous devez autoriser les comptes de travail SQL utilisés par Launchpad à se connecter à l’instance. Pour plus d’informations, consultez [SQLRUserGroup d’ajouter en tant qu’un utilisateur de base de données](../security/add-sqlrusergroup-to-database.md).

<a name="network"></a>

## <a name="add-network-protocols"></a>Ajouter des protocoles réseau

+ Activer les canaux nommés
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] utilise le protocole des canaux nommés pour les connexions entre les ordinateurs client et serveur, ainsi que pour certaines connexions internes. Si ce protocole n’est pas activé, vous devez l’installer et l’activer sur la machine virtuelle Azure et sur tous les clients de science des données susceptibles de se connecter au serveur.
  
+ Activer TCP/IP

  TCP/IP est requis pour les connexions de bouclage. Si vous obtenez l’erreur « DBNETLIB ; SQL Server n’existe pas ou l’accès refusé », activez TCP/IP sur l’ordinateur virtuel qui prend en charge de l’instance.