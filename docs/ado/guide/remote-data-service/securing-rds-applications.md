---
title: Sécurisation des Applications RDS | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS security [ADO]
ms.assetid: 82fb1330-d6c6-4c17-ad3e-d417ff822b25
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b2afe6074f115c1d9770251c51e6288e9d92ee3b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66699338"
---
# <a name="securing-rds-applications"></a>Sécurisation des applications RDS
Cette rubrique fournit des informations de sécurité de RDS.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="microsoft-internet-explorer-security-issues"></a>Problèmes de sécurité de Microsoft Internet Explorer  
 Grâce aux nouvelles améliorations de sécurité ajoutées à Microsoft Internet Explorer, certains objets ADO et des services Bureau à distance sont limitées à l’exécution uniquement dans un environnement en mode « sécurisée ». Cela nécessite que vous êtes conscient de ces problèmes, notamment les différentes zones, les niveaux de sécurité, comportement restrictif, les opérations non sécurisées et que vous les paramètres de sécurité personnalisés.  
  
## <a name="security-and-your-web-server"></a>Sécurité et votre serveur Web  
 Si vous utilisez le [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) objet sur votre serveur Web Internet, n’oubliez pas que cela comporte un risque de sécurité potentiel. Les utilisateurs externes qui obtiennent le nom de source de données valide (DSN), ID d’utilisateur et mot de passe pourrait écrire des pages pour envoyer une requête à la source de données. Si vous souhaitez un accès plus limité à une source de données, une option consiste à annuler l’inscription et de supprimer le **RDSServer.DataFactory** (msadcf.dll) et que vous utilisez à la place des objets métier personnalisés avec des requêtes codées en dur.  
  
 Pour plus d’informations sur les implications de sécurité de l’utilisation de l’objet RDSServer.DataFactory, consultez le Bulletin de sécurité Microsoft MS99-025 sur le site Web Microsoft sécurité.  
  
## <a name="client-impersonation-and-security"></a>Sécurité et emprunt d’identité du client  
 Si le **l’authentification du mot de passe** propriété de votre serveur Web IIS est définie pour l’authentification stimulation/réponse de Windows NT (pour Windows NT 4.0) ou pour l’authentification Windows intégrée (pour Windows 2000), puis sont des objets métier appelé sous le contexte de sécurité du client. Il s’agit d’une nouvelle fonctionnalité de RDS 1.5 qui permet l’emprunt d’identité du Client sur HTTP. Lorsque vous travaillez dans ce mode, l’ouverture de session sur le serveur Web (IIS) n’est pas anonyme, mais utilise l’ID utilisateur et le mot de passe que l’ordinateur client est en cours d’exécution sous. Si les DSN ODBC sont configurées pour utiliser une connexion approuvée, puis accès aux bases de données, telles que SQL Server, se produit également sous le contexte de sécurité du client. Mais cela ne fonctionne que si la base de données se trouve sur le même ordinateur que IIS ; les informations d’identification du client ne peut pas être reportées sur un autre ordinateur.  
  
 Par exemple, un client, John Doe, avec l’ID utilisateur = « JeanD » et le mot de passe = « secret » est connecté à un ordinateur client. Il exécute une application basée sur navigateur qui doit accéder à la **RDSServer.DataFactory** objet à créer un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) en exécutant une requête SQL sur l’ordinateur « MonServeur » exécutant IIS. MyServer, un système exécutant Windows NT Server 4.0, est configuré pour utiliser l’authentification stimulation/réponse de Windows NT, son DSN ODBC a « Utiliser une connexion approuvée » sélectionné et le serveur contient également la source de données SQL Server. Lorsqu’une demande est reçue sur le serveur Web, il demande au client pour l’ID utilisateur et le mot de passe. Par conséquent, la demande est consignée sur MonServeur comme provenant de « JeanD » / « Secret » au lieu de IUSER_MyServer (est la valeur par défaut lorsque l’authentification anonyme de mot de passe est activée). De même, lors de la connexion à SQL Server, « JeanD » / « Secret » est utilisé.  
  
 Par conséquent, le mode d’authentification stimulation/réponse de Windows NT IIS permet des pages HTML doit être créé sans que l’utilisateur en cours explicitement invité à entrer les informations d’ID et mot de passe utilisateur nécessaires pour vous connecter à la base de données. Si l’authentification de base IIS étaient utilisée, alors cela aussi est requis.  
  
## <a name="password-authentication"></a>Authentification de mot de passe  
 Services Bureau à distance peut communiquer avec un serveur Web IIS en cours d’exécution dans l’un des trois modes d’authentification de mot de passe : Authentification anonyme, Basic ou stimulation/réponse NT (appelée l’authentification Windows intégrée dans Windows 2000). Ces paramètres définissent comment de contrôle de l’accès par son intermédiaire, comme demander qu’un ordinateur client ont des privilèges d’accès explicites sur le serveur Web de NT d’un serveur Web.


