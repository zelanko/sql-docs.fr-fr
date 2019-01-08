---
title: Installer mssqlctl pour la gestion des clusters de données volumineuses SQL 2019 | Microsoft Docs
description: Découvrez comment installer l’outil mssqlctl pour l’installation et la gestion des clusters de données volumineuses de SQL Server 2019 (version préliminaire).
author: rothja
ms.author: jroth
manager: craigg
ms.date: 12/13/2018
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 5133134a45a4110abc0a1a7a3eebe1c5ac7b6ebd
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432102"
---
# <a name="install-mssqlctl-to-manage-sql-server-2019-big-data-clusters"></a>Installer mssqlctl pour gérer des clusters SQL Server 2019 big data

Cet article décrit comment installer le **mssqlctl** outil sur Windows ou Linux.

**mssqlctl** est un utilitaire de ligne de commande écrit dans Python que permet aux administrateurs de démarrer et de gérer le cluster de données volumineuses via les API REST de cluster. La version de Python minimale requise est v3.5. Vous devez également avoir `pip` qui est utilisé pour télécharger et installer **mssqlctl** outil. Les instructions ci-dessous fournissent des exemples pour Windows et Ubuntu. Pour l’installation de Python sur d’autres plateformes, consultez le [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download).

> [!IMPORTANT]
> Si vous avez installé une version antérieure de **mssqlctl**, vous devez supprimer le cluster *avant* la mise à niveau **mssqlctl** et l’installation de la nouvelle version. Pour plus d’informations, consultez [mise à niveau vers une nouvelle version](deployment-guidance.md#upgrade).

## <a id="windows"></a> Installation de mssqlctl Windows

1. Sur un client Windows, téléchargez le package Python nécessaire [ https://www.python.org/downloads/ ](https://www.python.org/downloads/). Pour python3.5.3 et versions ultérieures, pip3 est également installé lorsque vous installez Python. 

   > [!TIP] 
   > Lorsque vous installez Python3, sélectionnez cette option pour ajouter Python à votre **chemin d’accès**. Si vous ne le faites pas, vous pouvez êtes amené à constater où se trouve pip3 et l’ajouter manuellement à votre **chemin d’accès**.

1. Ouvrez une nouvelle session Windows PowerShell afin qu’il obtient le chemin d’accès plus récente avec Python qu’il contient.

2. Installer **mssqlctl** avec la commande suivante :

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl
   ```

## <a id="linux"></a> Installation de mssqlctl Linux

Sur Linux, vous devez installer Python 3.5 et ensuite mettre à niveau pip. L’exemple suivant montre les commandes qui fonctionneraient pour Ubuntu. Pour d’autres plateformes Linux, consultez le [documentation Python](https://wiki.python.org/moin/BeginnersGuide/Download).

1. Installer les packages Python nécessaires :

   ```bash
   sudo apt-get update && /
   sudo apt-get install -y python3 && /
   sudo apt-get install -y python3-pip && /
   sudo -H pip3 install --upgrade pip
   ```

1. Installer **mssqlctl** avec la commande suivante :

   ```bash
   pip3 install --extra-index-url https://private-repo.microsoft.com/python/ctp-2.2 mssqlctl
   ```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les clusters de données volumineuses, consultez [que sont les clusters de données volumineuses de SQL Server 2019 ?](big-data-cluster-overview.md).
