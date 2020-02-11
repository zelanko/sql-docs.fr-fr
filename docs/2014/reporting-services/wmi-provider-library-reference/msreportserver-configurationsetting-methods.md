---
title: Méthodes MSReportServer_ConfigurationSetting | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
api_name:
- MSReportServer_ConfigurationSetting Methods
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- WMI provider [Reporting Services], MSReportServer_ConfigurationSetting class
- MSReportServer_ConfigurationSetting class
ms.assetid: a08c2476-5b8e-4792-94da-1360fe231c6e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6d3fc7ae8ad4c3018bcc512296a670fdaac3b64e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66097354"
---
# <a name="msreportserver_configurationsetting-methods"></a>Méthodes MSReportServer_ConfigurationSetting
  La classe MSReportServer_ConfigurationSetting du Fournisseur WMI Report Server fournit les méthodes publiques suivantes.  
  
## <a name="public-methods"></a>M&#233;thodes publiques  
  
|||  
|-|-|  
|[BackupEncryptionKey](configurationsetting-method-backupencryptionkey.md)|Sauvegarde la clé de chiffrement pour l'instance. Un chiffrement par mot de passe est utilisé pour le stockage de la clé de chiffrement.|  
|[Méthode CreateSSLCertificateBinding &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-createsslcertificatebinding.md)|Crée une liaison de certificat SSL.|  
|[DeleteEncryptedInformation](configurationsetting-method-deleteencryptedinformation.md)|Supprime les informations chiffrées de la base de données du serveur de rapports.|  
|[DeleteEncryptionKey](configurationsetting-method-deleteencryptionkey.md)|Supprime les clés de chiffrement de la base de données du serveur de rapports.|  
|[GenerateDatabaseCreationScript](configurationsetting-method-generatedatabasecreationscript.md)|Génère un script SQL qui peut être utilisé pour créer la base de données du serveur de rapports.|  
|[GenerateDatabaseRightsScript](configurationsetting-method-generatedatabaserightsscript.md)|Génère un script SQL pouvant être utilisé pour accorder des autorisations d'utilisateurs à la base de données du serveur de rapports.|  
|[GenerateDatabaseUpgradeScript](configurationsetting-method-generatedatabaseupgradescript.md)|Génère un script SQL qui peut être utilisé pour mettre à niveau une base de données du serveur de rapports.|  
|[Méthode GetAdminSiteUrl &#40;WMI&#41;](configurationsetting-method-getadminsiteurl.md)|Obtient l'URL absolue vers le site Web Administration centrale.|  
|[GetDatabaseVersionDisplayName](configurationsetting-method-getdatabaseversiondisplayname.md)|Obtient le nom complet de la chaîne de version d'une base de données de serveur de rapports spécifique.|  
|[InitializeReportServer](configurationsetting-method-initializereportserver.md)|Initialise l'instance de serveur de rapports spécifiée.|  
|[Méthode ListInstalledSharePointVersions &#40;WMI&#41;](configurationsetting-method-listinstalledsharepointversions.md)|Retourne un ensemble de jetons qui représentent les versions [!INCLUDE[winSPServ](../../includes/winspserv-md.md)] [!INCLUDE[offSPServ](../../includes/offspserv-md.md)]de Microsoft, [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], ou [!INCLUDE[SPS2010](../../includes/sps2010-md.md)] installées sur le même ordinateur que le serveur de rapports.|  
|[Méthode ListIPAddresses &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listipaddresses.md)|Répertorie les adresses IP de l'ordinateur.|  
|[ListReportServersInDatabase](configurationsetting-method-listreportserversindatabase.md)|Retourne une liste des installations du serveur de rapports qui sont présentes dans la base de données du serveur de rapports, même si ces installations n'ont pas accès aux informations sécurisées.|  
|[Méthode ListReservedURLs &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listreservedurls.md)|Répertorie les URL réservées pour toutes les applications sur le serveur de rapports.|  
|[Méthode ListSSLCertificateBindings &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listsslcertificatebindings.md)|Répertorie les liaisons de certificats SSL qui existent dans HTTP.SYS et celles attendues de RSReportServer.config.|  
|[Méthode ListSSLCertificates &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-listsslcertificates.md)|Répertorie les certificats SSL installés sur l'ordinateur.|  
|[ReencryptSecureInformation](configurationsetting-method-reencryptsecureinformation.md)|Génère une nouvelle clé de chiffrement et rechiffre toutes les informations sécurisées dans la base de données du serveur de rapports à l'aide de cette nouvelle clé.|  
|[Méthode RemoveSSLCertificateBindings &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-removesslcertificatebinding.md)|Supprime une liaison de certificat SSL.|  
|[RemoveUnattendedExecutionAccount](configurationsetting-method-removeunattendedexecutionaccount.md)|Supprime l'entrée de compte d'exécution sans assistance de la configuration du serveur de rapports.|  
|[Méthode RemoveURL &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-removeurl.md)|Supprime une URL réservée pour le serveur de rapports.|  
|[Méthode re&#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-reserveurl.md)|Ajoute une réservation d'URL pour une application donnée.|  
|[RestoreEncryptionKey](configurationsetting-method-restoreencryptionkey.md)|Réapplique la clé de chiffrement spécifiée à la base de données du serveur de rapports.|  
|[SetDatabaseConnection](configurationsetting-method-setdatabaseconnection.md)|Définit la connexion à une base de données de serveur de rapports spécifique.|  
|[SetDatabaseLogonTimeout](configurationsetting-method-setdatabaselogontimeout.md)|Spécifie la valeur du délai d'attente par défaut pour les tentatives d'ouverture de session de base de données du serveur de rapports.|  
|[SetDatabaseQueryTimeout](configurationsetting-method-setdatabasequerytimeout.md)|Spécifie la valeur de délai par défaut pour les requêtes sur la base de données du serveur de rapports.|  
|[SetEmailConfiguration](configurationsetting-method-setemailconfiguration.md)|Configure l'extension de remise par messagerie utilisée par le serveur de rapports pour envoyer des messages électroniques.|  
|[SetSecureConnectionLevel](configurationsetting-method-setsecureconnectionlevel.md)|Définit le niveau de connexion sécurisée du serveur de rapports.|  
|[SetServiceState](configurationsetting-method-setservicestate.md)|Active ou désactive le service Report Server.|  
|[SetUnattendedExecutionAccount](configurationsetting-method-setunattendedexecutionaccount.md)|Spécifie le compte utilisé pour exécuter les rapports sans assistance.|  
|[Méthode SetVirtualDirectory &#40;WMI MSReportServer_ConfigurationSetting&#41;](configurationsetting-method-setvirtualdirectory.md)|Définit le répertoire virtuel pour une application.|  
|[SetWindowsServiceIdentity](configurationsetting-method-setwindowsserviceidentity.md)|Fait en sorte que le service Report Server s'exécute en tant que l'utilisateur Windows spécifié et accorde des autorisations de système de fichiers suffisantes à ce compte pour permettre au serveur de rapports de fonctionner.|  
  
## <a name="see-also"></a>Voir aussi  
 [Classe MSReportServer_ConfigurationSetting](msreportserver-configurationsetting-class.md)  
  
  
