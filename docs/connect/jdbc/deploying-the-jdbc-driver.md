---
title: Déploiement du pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b688e5b014915578df5c56ec5e6af2fc8fe26b16
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66781981"
---
# <a name="deploying-the-jdbc-driver"></a>Déploiement du pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Quand vous déployez une application qui dépend du [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], vous devez redistribuer le pilote JDBC avec votre application. Contrairement à Windows DAC (Windows Data Access Components), qui est un composant du système d’exploitation de Windows, le pilote JDBC est considéré comme un composant de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Il existe deux méthodes pour déployer le pilote JDBC avec votre application. La première consiste à inclure les fichiers du pilote JDBC dans votre propre package d'installation. La seconde implique l’utilisation du package d’installation JDBC fourni par Microsoft, que vous pouvez télécharger à partir du [Centre de développement Microsoft JDBC Driver for SQL Server](https://go.microsoft.com/fwlink/?LinkId=70166).  
  
 Les sections suivantes présentent l'utilisation du package d'installation JDBC sur les systèmes d'exploitation Windows et UNIX.  
  
> [!NOTE]  
>  Pour obtenir des informations sur le déploiement d'applications Java en général, consultez le site de Java.  
  
## <a name="deploying-the-jdbc-driver-on-windows-systems"></a>Déploiement du pilote JDBC sur les systèmes Windows  
 Quand vous déployez le pilote JDBC sur des systèmes d’exploitation Windows, vous devez utiliser la version du fichier zip exécutable du package d’installation, généralement appelée `sqljdbc_<version>_<language>.exe`.  
  
 Pour exécuter le fichier zip exécutable en mode silencieux, vous devez utiliser l’option de ligne de commande `/auto` sur la ligne de commande ou dans un fichier de commandes, comme indiqué ci-après :  
  
 `sqljdbc_<version>_<language>.exe /auto`  
  
> [!NOTE]  
>  Quand vous utilisez l’option `/auto`, il ne s’agit pas réellement d’une installation en mode silencieux, car une boîte de dialogue WinZip s’affiche néanmoins sur l’écran de l’utilisateur. Cependant, vous devez l'ignorer ; cette boîte de dialogue se fermera dès que l'opération de décompression sera terminée.  
  
## <a name="deploying-the-driver-on-unix-systems"></a>Déploiement du pilote sur les systèmes UNIX  
 Quand vous déployez le pilote JDBC sur des systèmes d’exploitation UNIX, vous devez utiliser la version du fichier gzip du package d’installation, qui est généralement appelée `sqljdbc_<version>_<language>.tar.gz`.  
  
 Avant d'installer le pilote JDBC, assurez-vous que les utilitaires gzip et tar sont installés sur le système de l'utilisateur et que les dossiers contenant les exécutables des deux utilitaires sont ajoutés à la variable d'environnement PATH.  
  
 Pour décompresser le fichier d'archive tar, accédez au répertoire dans lequel vous souhaitez décompresser le pilote, puis tapez la commande suivante :  
  
 `gzip -d sqljdbc_<version>_<language>.tar.gz`  
  
 Pour décompresser le fichier d'archive tar, déplacez-le vers le répertoire dans lequel vous souhaitez installer le pilote, puis tapez la commande suivante :  
  
 `tar -xf sqljdbc_<version>_<language>.tar`  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
