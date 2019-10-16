---
title: Notes de publication de SQL Server 2019 | Microsoft Docs
ms.date: 10/07/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: release-landing
ms.topic: article
ms.assetid: 13942af8-5a40-4cef-80f5-918386767a47
author: MikeRayMSFT
ms.author: mikeray
monikerRange: = sql-server-ver15 || = sqlallproducts-allversions
ms.openlocfilehash: 9b6895abfa0b09459911eba03b52837379f2d162
ms.sourcegitcommit: 512acc178ec33b1f0403b5b3fd90e44dbf234327
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72041189"
---
# <a name="sql-server-2019-preview-release-notes"></a>Notes de publication de SQL Server 2019 Preview
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article décrit les limitations et les problèmes connus pour [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]. Pour des informations connexes, consultez :

>[Nouveautés de SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md)

>[!NOTE]
>Le contenu est publié pour la version Release Candidate [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]. La version Release Candidate est un logiciel en version préliminaire. Les informations peuvent faire l’objet de modification. Pour plus d’informations sur les scénarios de support, consultez [Support](#support).

## <a name="includesql-server-2019includessssqlv15-mdmd-release-candidate-rc"></a>Version Release Candidate (RC) [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]

RC [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] est la dernière version publique de [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

RC [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] est disponible uniquement en édition d’évaluation. Aucune autre édition n’est disponible.

Vous trouverez les détails complets de la prise en charge et de la gestion des licences pour les versions Release Candidate dans `license_Eval.rtf` sur votre support d’installation.

[!INCLUDE[ctp-support-exclusion](../includes/ctp-support-exclusion.md)]

## <a name="documentation"></a>Documentation

- **Problème et impact sur le client** : la documentation pour SQL Server 2019 (15.x) est limitée, et le contenu est inclus avec l’ensemble de documentation [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]. Dans les articles, le contenu propre à SQL Server 2019 (15.x) est noté avec **S’applique à**.

- **Problème et impact sur le client** : la documentation [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut être filtrée par version. Utilisez le contrôle en haut à gauche de chaque page de documentation pour filtrer selon vos besoins.

- **Problème et impact sur le client** : aucun contenu hors connexion n’est disponible pour SQL Server 2019 (15.x).

## <a name="build-number"></a>Numéro de build

Le numéro de build pour SQL Server 2019 RC sur Windows, Linux et les conteneurs est `15.0.1900.25`.  Le numéro de build pour SQL Server 2019 RC utilisé dans les clusters Big Data est `15.0.1900.47`.

## <a name="hardware-and-software-requirements"></a>Configuration matérielle et logicielle requise

- **Problème et impact sur le client** : la configuration matérielle et logicielle requise est en cours d’examen et n’est pas finalisée pour la sortie du produit.

  - **Matériel**
    - [Windows : processeur, mémoire et système d’exploitation requis](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#pmosr)
    - [Linux : configuration système requise](../linux/sql-server-linux-setup.md#system)
  - **Logiciels**
    - Windows Server 2016 ou version ultérieure. Pour connaître la configuration requise supplémentaire, consultez [Configuration requise pour l’installation de SQL Server](../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).
    - Microsoft .NET Framework 4.6.2. Disponible sur le [Centre de téléchargement](https://www.microsoft.com/download/details.aspx?id=53344).
    - Pour Linux, reportez-vous à [Linux : plateformes prises en charge](../linux/sql-server-linux-setup.md#supportedplatforms).

## <a name="sql-server-installation-may-fail-if-ssms-18x-is-installed"></a>L’installation de SQL Server peut échouer si SSMS 18.x est installé

- **Problème et impact sur le client** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] l’installation échoue lorsque les installations suivantes sont effectuées dans cet ordre :
  1. SQL Server Management Studio (SSMS) version 18.0, 18.1, 18.2 ou 18.3 est installé sur le serveur.
  1. Une tentative d’installation de [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] est effectuée à partir d’un support amovible. Par exemple, le support d’installation est un DVD.

- **Solution de contournement**:
  1. Désinstallez toute version de SSMS antérieure à SSMS 18.3.1.
  1. Installez une version plus récente de SSMS (18.3.1 ou une version ultérieure). Pour obtenir la dernière version, consultez [Télécharger SSMS](../ssms/download-sql-server-management-studio-ssms.md).
  1. Installez [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] normalement.

  >[!NOTE]
  >La désinstallation est requise.

- **S’applique à** : version finale (RC) de [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)].

## <a name="updated-compiler"></a>Compilateur mis à jour

- **Problème et impact sur le client** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] est construit avec un compilateur mis à jour. CTP 2.1 disposait d’une erreur connue où les résultats de scénarios de conversion ou à virgule flottante retournaient une valeur différente des versions précédentes à cause du compilateur mis à jour. CTP 2.2 inclut une solution qui veille à ce que les scénarios concernés retournent les mêmes résultats que les versions précédentes de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. À compter de la version Release Candidate, nous n’avons connaissance d’aucun problème. Veuillez signaler toute anomalie de résultat comparé à [!INCLUDE[ss2017](../includes/sssqlv14-md.md)] à l’équipe [[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]](https://aka.ms/sqlfeedback) sans tarder.

- **Solution de contournement**: Néant

- **S’applique à** : Version Release Candidate

## <a name="installation-wizard-may-wait-between-eula-pages"></a>L’Assistant Installation peut attendre entre les pages du CLUF

- **Problème et impact sur le client** : Pendant l’installation avec l’Assistant Installation, le processus peut attendre pendant une durée prolongée entre le contrat de licence utilisateur final (CLUF) pour R Services et le CLUF pour Python.

- **Solution de contournement**: attendez que l’Assistant Installation continue. Le délai d’attente peut dépasser 30 minutes.

- **S’applique à** : CTP 3.0 [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]

## <a name="utf-8-collations"></a>Classements UTF-8

- **Problème et impact sur le client** : les classements prenant en charge UTF-8 ne peuvent pas être utilisés avec certaines fonctionnalités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. UTF-8 n’est pas pris en charge quand les fonctionnalités [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] suivantes sont en cours d’utilisation :

  - OLTP en mémoire
  - Table externe pour PolyBase ([!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] RC 1)
  - Always Encrypted (jusqu’à [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] RC 1)
  - Serveurs liés (jusqu’à [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2)

  > [!Note]
  > Actuellement, l’interface utilisateur d’Azure Data Studio et de SQL Server Data Tools (SSDT) ne permet pas de choisir des classements prenant en charge UTF-8. Il en va différemment de l’interface utilisateur de la dernière version 18 de [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] SSMS.
 
- **Solution de contournement**: aucune pour [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP (toutes versions).


- **S’applique à** : Toutes les versions CTP.

## <a name="always-encrypted-with-secure-enclaves"></a>Always Encrypted avec enclaves sécurisées

- **Problème et impact sur le client** : Les calculs avancés sont des optimisations de performances et des améliorations de gestion des erreurs en attente d’optimisation. Ils sont actuellement désactivées par défaut.

- **Solution de contournement**: pour activer les calculs avancés, exécutez `DBCC traceon(127,-1)`. Pour plus d’informations, consultez [Activer les calculs avancés](../relational-databases/security/encryption/configure-always-encrypted-enclaves.md#configure-a-secure-enclave).

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.2, CTP 3.1

## <a name="sql-server-configuration-manager-may-not-start"></a>Il est possible que le Gestionnaire de configuration SQL Server ne démarre pas

- **Problème et impact sur le client** : Le Gestionnaire de Configuration SQL Server (SSCM) ne démarre pas sur une machine sans le fichier du VCRuntime 140 (VCRUNTIME140.dll). Lorsque vous démarrez SSCM, l’utilisateur peut voir la boîte de dialogue suivante : 


  `MMC could not create the snap-in. The snap-in might not have been installed correctly.`

- **Solution de contournement**:  installez la dernière version de VC Runtime 2013 (x86) :

  - [Verbose](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)
  - [Direct](https://support.microsoft.com/help/4032938/update-for-visual-c-2013-redistributable-package)

- **S’applique à** : [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] CTP 3.1, CTP 3.0, CTP 2.5.

## <a name="always-on-availability-group-kubernetes-operator-not-supported"></a>L’opérateur de groupe de disponibilité Always On Kubernetes n’est pas pris en charge.

- **Problème et impact sur le client** : L’opérateur Kubernetes pour les groupes de disponibilité Always On n’est pas pris en charge dans cette version Release Candidate et ne sera pas disponible dans la version finale. 

- **Solution de contournement**: None

- **S’applique à** : Version Release Candidate [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]

## <a name="master-data-service-notification-email-contains-broken-link"></a>L’e-mail de notification Master Data Services contient un lien rompu

- **Problème et impact sur le client** : L’e-mail de notification Master Data Services (MDS) contient un lien rompu. Le lien accède à une page qui retourne une erreur semblable au message suivant :

   `The view 'Index' or its master was not found or no view engine supports the searched locations.`

- **Solution de contournement**: Ouvrez le portail MDS et accédez à la ressource manuellement.

- **S’applique à** : Version Release Candidate de SQL Server 2019

## <a name="machine-learning-services"></a>Machine Learning Services

Pour les problèmes rencontrés dans SQL Server Machine Learning Services, consultez [Problèmes connus dans SQL Server Machine Learning Services](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md).

[!INCLUDE[get-help-options-msft-only](../includes/paragraph-content/get-help-options.md)]

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png)
