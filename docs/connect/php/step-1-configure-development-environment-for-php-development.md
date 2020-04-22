---
title: 'Étape 1 : Configurer un environnement pour PHP'
description: L’étape 1 de ce guide de prise en main implique l’installation de PHP et de Microsoft ODBC Driver for SQL Server, et la configuration de votre environnement de développement.
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 0bce6022-00bd-45c6-9671-eaa9dfa395a8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 88eb2c2c67eac3ecd9fba2c79c143de28cf60d22
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81633170"
---
# <a name="step-1-configure-environment-for-php-development"></a>Étape 1 : Configurer un environnement de développement PHP
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]




* Identifiez la version du pilote PHP que vous allez utiliser, en fonction de votre environnement :  [Configuration système requise pour Microsoft Drivers for PHP for SQL Server](system-requirements-for-the-php-sql-driver.md)
* Téléchargez ici et installez le pilote PHP applicable : [Télécharger le pilote PHP Microsoft](https://www.microsoft.com/download/details.aspx?id=20098)  
* Téléchargez ici et installez le pilote ODBC applicable :  [Télécharger un pilote ODBC pour SQL Server](../odbc/download-odbc-driver-for-sql-server.md)  
* Configurez le pilote PHP et le serveur web en fonction de votre système d’exploitation :

### <a name="windows"></a>Windows  
  

* Configurez le chargement du pilote PHP : [Chargement de Microsoft Drivers for PHP for SQL Server](../../connect/php/loading-the-php-sql-driver.md) 
* Configurez IIS de façon à héberger des applications PHP : [Configurer IIS pour les pilotes Microsoft pour PHP pour SQL Server](../../connect/php/configuring-iis-for-php-sql-driver.md)

### <a name="linux-and-macos"></a>Linux et macOS


*   Configurez le chargement du pilote PHP et paramétrez votre serveur web de façon à héberger des applications PHP : [Tutoriel d’installation des pilotes PHP pour macOS et Linux](../../connect/php/installation-tutorial-linux-mac.md)
