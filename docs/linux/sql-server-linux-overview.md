---
title: "Vue d’ensemble de SQL Server sur Linux | Documents Microsoft"
description: "Cette rubrique décrit comment SQL Server s’exécute sur Linux et fournit des informations sur la façon d’en savoir plus."
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 12/21/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 9dcc6a90-0add-42c2-815b-862e4e2a21ac
ms.workload: Active
ms.openlocfilehash: a17c62aeddd0ed898d2a43931965bb7052a58412
ms.sourcegitcommit: 73043fe1ac5d60b67e33b44053c0a7733b98bc3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="sql-server-on-linux"></a>SQL Server sur Linux

SQL Server 2017 s’exécute désormais sur Linux. Il est le même moteur de base de données SQL Server, de nombreuses fonctionnalités et des services, quel que soit votre système d’exploitation similaire.

## <a name="install"></a>Install

Pour commencer, installez SQL Server sur Linux à l’aide d’un des Démarrages rapides suivants :

- [Installer sur Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
- [Installer sur SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
- [Installer sur Ubuntu](quickstart-install-connect-ubuntu.md)
- [Exécutez sur Docker](quickstart-install-connect-docker.md)
- [Approvisionner une machine virtuelle SQL dans Azure](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=%2fsql%2flinux%2ftoc.json)

> [!NOTE]
> Docker lui-même s’exécute sur plusieurs plateformes, ce qui signifie que vous pouvez exécuter l’image Docker sur Windows, Mac et Linux.

## <a name="connect"></a>Se connecter

Après l’installation, connectez-vous à l’instance de SQL Server sur l’ordinateur Linux. Vous pouvez vous connecter localement ou à distance et avec un large éventail d’outils et de pilotes. Les Démarrages rapides montrent comment utiliser le [sqlcmd](sql-server-linux-setup-tools.md) outil de ligne de commande. Autres outils sont les suivantes :

| Outil | Didacticiel |
|-----|-----|
| Visual Studio Code (Code de Visual Studio) | [Utilisation de Code de Visual Studio avec SQL Server sur Linux](sql-server-linux-develop-use-vscode.md) |
| SQL Server Management Studio (SSMS) | [Utilisez SSMS sur Windows pour se connecter à SQL Server sur Linux](sql-server-linux-develop-use-ssms.md) |
| Outils de données SQL Server (SSDT) | [Utiliser SSDT avec SQL Server sur Linux](sql-server-linux-develop-use-ssdt.md) |

## <a name="explore"></a>Explorer

SQL Server 2017 a le même moteur de base de données sous-jacente sur toutes les plateformes prises en charge, y compris Linux. Autant de fonctionnalités et de fonctionnalités existantes fonctionnent de la même façon sur Linux. Cette zone de la documentation expose certaines de ces fonctionnalités à partir d’une perspective de Linux. Il appelle également les zones qui ont des exigences uniques sur Linux.

Si vous êtes déjà familiarisé avec SQL Server, passez en revue les [notes de publication](sql-server-linux-release-notes.md) pour des recommandations générales et les problèmes connus pour cette version. Observez [quelles sont les nouveautés de SQL Server sur Linux](sql-server-linux-whats-new.md) ainsi que [Nouveautés 2017 du serveur SQL globale](../sql-server/what-s-new-in-sql-server-2017.md). Pour obtenir des réponses aux questions fréquemment posées, consultez le [SQL Server sur le Forum aux questions sur Linux](sql-server-linux-faq.md).

##  <a name="infotipmediageneralinfotippng-engage-with-the-sql-server-engineering-team"></a>![info_tip](./media/general/info_tip.png) Contacter l’équipe d’ingénierie de SQL Server

- [Échange de pile DBA](https://dba.stackexchange.com/questions/tagged/sql-server): poser des questions d’administration de base de données
- [Dépassement de capacité de la pile](http://stackoverflow.com/questions/tagged/sql-server): poser des questions sur le développement
- [Forums MSDN](https://social.msdn.microsoft.com/Forums/en-US/home?category=sqlserver): poser des questions techniques
- [Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback): signaler des bogues et la fonctionnalité de demande
- [Reddit](https://www.reddit.com/r/SQLServer/): traitent de SQL Server
