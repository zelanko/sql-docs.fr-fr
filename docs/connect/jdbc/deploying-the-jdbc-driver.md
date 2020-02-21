---
title: Déploiement du pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 10/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3ad3508d-d9b1-47fb-a63b-21cdc3ed44e0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 518f6bd2605d92857520f870b20edcd351771c54
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "73049836"
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

## <a name="legalities-of-driver-redistribution"></a>Aspects juridiques de la redistribution des pilotes

Les versions 6.0, 6.2, 6.4 et 7.0 du pilote JDBC sont redistribuables. Lisez la clause _Code distribuable_ des contrats de licence.

Les versions 4.x du pilote JDBC sont anciennes et obsolètes. La prise en charge de 4.x a expiré avant 2018.

## <a name="see-also"></a>Voir aussi  
 [Présentation du pilote JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
