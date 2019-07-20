---
title: Installer les fonctionnalités de langage R et Python sur une machine virtuelle Azure
description: Exécutez les solutions de science des données R et Python et de Machine Learning sur une machine virtuelle SQL Server dans le Cloud Azure.
ms.prod: sql
ms.technology: machine-learning
ms.date: 11/09/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 6f034f3a766e4f82bd1bcfd182f4eee285f7f829
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345043"
---
# <a name="install-sql-server-machine-learning-services-with-r-and-python-on-an-azure-virtual-machine"></a>Installer SQL Server Machine Learning Services avec R et Python sur une machine virtuelle Azure
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Vous pouvez installer l’intégration R et Python avec Machine Learning Services sur une machine virtuelle SQL Server dans Azure, en éliminant les tâches d’installation et de configuration. Une fois l’ordinateur virtuel déployé, les fonctionnalités sont prêtes à l’emploi.
 
Pour obtenir des instructions pas à pas, consultez [Comment configurer une machine virtuelle Windows SQL Server dans le portail Azure](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision).

L’étape [configurer les paramètres SQL Server](https://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-server-provision#3-configure-sql-server-settings) est l’endroit où vous ajoutez des machine learning à votre instance.

<a name="firewall"></a>

## <a name="unblock-the-firewall"></a>Débloquer le pare-feu

Par défaut, le pare-feu sur la machine virtuelle Azure comprend une règle qui bloque l’accès réseau pour les comptes d’utilisateurs locaux.

Vous devez désactiver cette règle pour vous assurer que vous pouvez accéder [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’instance à partir d’un client de science des données distant.  Sinon, votre code Machine Learning ne peut pas s’exécuter dans des contextes de calcul qui utilisent l’espace de travail de la machine virtuelle.

Pour activer l’accès à partir de clients de science des données distants:

1. Sur la machine virtuelle, ouvrez le Pare-feu Windows avec fonctions avancées de sécurité.
2. Sélectionnez **Règles sortantes**.
3. Désactivez la règle suivante :
  
     `Block network access for R local user accounts in SQL Server instance MSSQLSERVER`
  
## <a name="enable-odbc-callbacks-for-remote-clients"></a>Autoriser les rappels ODBC pour les clients distants

Si vous vous attendez à ce que les clients qui appellent le serveur doivent émettre des requêtes ODBC dans le cadre de leurs solutions Machine Learning, vous devez vous assurer que le Launchpad peut effectuer des appels ODBC pour le compte du client distant. 

Pour cela, vous devez autoriser les comptes de travail SQL utilisés par Launchpad à se connecter à l’instance. Pour plus d’informations, consultez [Ajouter SQLRUserGroup en tant qu’utilisateur de base de données](../security/create-a-login-for-sqlrusergroup.md).

<a name="network"></a>

## <a name="add-network-protocols"></a>Ajouter des protocoles réseau

+ Activer les canaux nommés
  
  [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] utilise le protocole des canaux nommés pour les connexions entre les ordinateurs client et serveur, ainsi que pour certaines connexions internes. Si ce protocole n’est pas activé, vous devez l’installer et l’activer sur la machine virtuelle Azure et sur tous les clients de science des données susceptibles de se connecter au serveur.
  
+ Activation de TCP/IP

  TCP/IP est requis pour les connexions de bouclage. Si vous recevez l’erreur «DBNETLIB; SQL Server n’existe pas ou l’accès est refusé», activez TCP/IP sur la machine virtuelle qui prend en charge l’instance.