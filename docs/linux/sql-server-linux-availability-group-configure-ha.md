---
title: "Konfigurieren der verfügbarkeitsgruppe für SQL Server on Linux | Microsoft Docs"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3a94bf7646143d687a7300c8ab2a66c3caa2d8d9
ms.contentlocale: de-de
ms.lasthandoff: 08/02/2017

---

# <a name="configure-always-on-availability-group-for-sql-server-on-linux"></a>Konfigurieren von Always On-verfügbarkeitsgruppe für SQL Server on Linux

Dieser Artikel beschreibt, wie eine SQL Server AlwaysOn für die verfügbarkeitsgruppe für hohe Verfügbarkeit unter Linux erstellt wird. Es gibt zwei Konfigurationstypen für Verfügbarkeitsgruppen. Ein *hohe Verfügbarkeit* Konfiguration verwendet einen Cluster-Manager für die Geschäftskontinuität bereitstellen. Diese Konfiguration kann auch schreibgeschützte mit horizontaler Skalierung Replikate enthalten. Dieses Dokument erläutert, wie die hohe Verfügbarkeit der verfügbarkeitsgruppenkonfiguration erstellt wird.

Sie können auch erstellen eine *Lesen mit horizontaler Skalierung* verfügbarkeitsgruppe ohne einen Cluster-Manager. Diese Konfiguration bietet nur schreibgeschützte Replikate für dezentrales Skalieren der Leistung. Es bietet keine hohen Verfügbarkeit. Um eine verfügbarkeitsgruppe für schreibgeschützte mit horizontaler Skalierung zu erstellen, finden Sie unter [konfigurieren, die verfügbarkeitsgruppe mit horizontaler Skalierung für SQL Server on Linux lesen](sql-server-linux-availability-group-configure-rs.md).

Konfigurationen, die hohe Verfügbarkeit und Datenschutz gewährleisten erfordern zwei oder drei synchrone Replikate commit. Mit drei synchroner Replikate die verfügbarkeitsgruppe können automatisch wiederherstellen, selbst wenn ein Server nicht verfügbar ist. Weitere Informationen finden Sie unter [hohe Verfügbarkeit und Datenschutz für verfügbarkeitsgruppenkonfigurationen](sql-server-linux-availability-group-ha.md). 

Alle Server müssen entweder physisch oder virtuell sein, und virtuelle Server muss auf die gleiche Virtualisierungsplattform. Diese Anforderung ist, da die Agents Zäune plattformspezifisch sind. Finden Sie unter [Richtlinien für einen Gastcluster](https://access.redhat.com/articles/29440#guest_policies).

## <a name="roadmap"></a>Roadmap für die

Die Schritte zum Erstellen einer verfügbarkeitsgruppe auf Linux-Servern zwecks hoher Verfügbarkeit unterscheiden sich von den Schritten in einem Windows Server-Failovercluster. Die folgende Liste beschreibt auf hoher Ebene die Schritte aus: 

1. [Konfigurieren von SQL Server auf drei Clusterservern](sql-server-linux-setup.md).

   >[!IMPORTANT]
   >Alle drei Server in der verfügbarkeitsgruppe müssen auf der gleichen Plattform - physisch oder virtuell - werden, da Linux hoher Verfügbarkeit Zäune-Agents verwendet, um Ressourcen auf den Servern zu isolieren. Die Agents Zäune sind für jede Plattform spezifisch.

2. Erstellen Sie die Verfügbarkeitsgruppe. Dieser Schritt wird in diesem Artikel aktuelle behandelt. 

3. Konfigurieren eines Cluster-Ressourcen-Managers wie Schrittmacher an.
   
   Die Möglichkeit zum Konfigurieren eines Cluster-Ressourcen-Managers, hängt von der bestimmten Linux-Distribution ab. Finden Sie unter den folgenden Links für spezifische Anweisungen Verteilung: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   * [SUSE](sql-server-linux-availability-group-cluster-sles.md)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   >[!IMPORTANT]
   >Produktionsumgebungen sind einen Fencing-Agent, wie STONITH für hohe Verfügbarkeit erforderlich. Die Demos in dieser Dokumentation verwenden Zäune-Agents. Die Demos sind für das Testen und nur die Überprüfung. 
   
   >Ein Linux-Cluster verwendet Fencing, um den Cluster in einen bekannten Zustand zurückzugeben. Die Methode zum Konfigurieren von Fencing hängt davon ab, die Verteilung und der Umgebung. Derzeit ist Fencing nicht in einige Cloudumgebungen verfügbar. Weitere Informationen finden Sie unter [Richtlinien zur Unterstützung für RHEL hohe Verfügbarkeit Cluster - Virtualisierungsplattformen](https://access.redhat.com/articles/29440).
   
   >SLES, finden Sie unter [SUSE Linux Enterprise-Erweiterung für hohe Verfügbarkeit](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing).

5. Fügen Sie der verfügbarkeitsgruppe als Ressource im Cluster.  

   Die Möglichkeit, die verfügbarkeitsgruppe als Ressource im Cluster hinzufügen, hängt von der Linux-Distribution ab. Finden Sie unter den folgenden Links für spezifische Anweisungen Verteilung: 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)
   * [SLES](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)

[!INCLUDE [Create Prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>Erstellen der verfügbarkeitsgruppe.

Es gibt zwei unterstützte verfügbarkeitsgruppenkonfigurationen für SQL Server on Linux.

- [Drei synchroner Replikate](sql-server-linux-availability-group-ha.md#threeSynch)

- [Zwei synchrone Replikate](sql-server-linux-availability-group-ha.md#twoSynch)

Informationen finden Sie unter [hohe Verfügbarkeit und Datenschutz für verfügbarkeitsgruppenkonfigurationen](sql-server-linux-availability-group-ha.md).

Erstellen Sie die verfügbarkeitsgruppe für hohe Verfügbarkeit unter Linux. Verwenden der [CREATE AVAILABILITY GROUP](https://docs.microsoft.com/en-us/sql/t-sql/statements/create-availability-group-transact-sql) mit `CLUSTER_TYPE = EXTERNAL`. 

* Verfügbarkeitsgruppe – `CLUSTER_TYPE = EXTERNAL` gibt an, dass eine externe Cluster-Entität die verfügbarkeitsgruppe verwaltet. Schrittmacher ist ein Beispiel für eine externe Cluster-Entität. Wenn der Verfügbarkeit Cluster Gruppentyp extern ist, 

* Legen Sie die primären und sekundäre Replikaten `FAILOVER_MODE = EXTERNAL`. 
   Gibt an, dass das Replikat mit einem externen Cluster-Manager, z. B. Schrittmacher interagiert. 

Die folgende Transact-SQL-Skripts erstellt eine verfügbarkeitsgruppe für hohe Verfügbarkeit, die mit dem Namen `ag1`. Das Skript konfiguriert die verfügbarkeitsgruppenreplikaten mit `SEEDING_MODE = AUTOMATIC`. Diese Einstellung bewirkt, dass SQL Server die Datenbank automatisch in jeder sekundären Serverinstanz erstellt. Aktualisieren Sie das folgende Skript für Ihre Umgebung. Ersetzen Sie die `**<node1>**`, und `**<node2>**` Werte mit den Namen der SQL Server-Instanzen, die die Replikate hosten. Ersetzen Sie die `**<5022>**` mit dem Port, den Sie für die datenbankspiegelungs-Endpunkt Daten festlegen. Um die verfügbarkeitsgruppe zu erstellen, führen Sie die folgende Transact-SQL für die SQL Server-Instanz, die das primäre Replikat hostet.

Führen Sie **nur eine** der folgenden Skripts: 

- Erstellen Sie verfügbarkeitsgruppe mit drei synchronen Replikaten.

   ```Transact-SQL
   CREATE AVAILABILITY GROUP [ag1]
       WITH (DB_FAILOVER = ON, CLUSTER_TYPE = EXTERNAL)
       FOR REPLICA ON
           N'**<node1>**' 
            WITH (
               ENDPOINT_URL = N'tcp://**<node1>:**<5022>**',
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'**<node2>**' 
            WITH ( 
               ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**', 
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'**<node3>**'
           WITH( 
              ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**', 
              AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
              FAILOVER_MODE = EXTERNAL,
              SEEDING_MODE = AUTOMATIC
              );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```

   >[!IMPORTANT]
   >Führen Sie nach dem Ausführen dieses Skript zum Erstellen einer verfügbarkeitsgruppe mit drei synchronen Replikate nicht das folgende Skript aus:

<a name="readScale"></a>

- Erstellen Sie die verfügbarkeitsgruppe mit zwei synchronen Replikaten

   Zwei Replikate mit den Verfügbarkeitsmodus für synchrone einschließen. Das folgende Skript erstellt z. B. eine verfügbarkeitsgruppe namens `ag1`. `node1`und `node2` Replikate im synchronen Modus mit automatischem seeding und automatisches Failover zu hosten.

   >[!IMPORTANT]
   >Führen Sie nur das folgende Skript zum Erstellen einer verfügbarkeitsgruppe mit zwei synchronen Replikaten. Das folgende Skript kann nicht ausgeführt werden, wenn Sie dieses Skript ausgeführt haben. 

   ```Transact-SQL
   CREATE AVAILABILITY GROUP [ag1]
      WITH (CLUSTER_TYPE = EXTERNAL)
      FOR REPLICA ON
      N'node1' WITH (
         ENDPOINT_URL = N'tcp://node1:5022',
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
         FAILOVER_MODE = EXTERNAL,
         SEEDING_MODE = AUTOMATIC
      ),
      N'node2' WITH ( 
         ENDPOINT_URL = N'tcp://node2:5022', 
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
         FAILOVER_MODE = EXTERNAL,
         SEEDING_MODE = AUTOMATIC
      );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```


Sie können auch konfigurieren eine verfügbarkeitsgruppe mit `CLUSTER_TYPE=EXTERNAL` mit SQL Server Management Studio oder PowerShell. 

### <a name="join-secondary-replicas-to-the-availability-group"></a>Verknüpfen Sie sekundärer Replikate mit der verfügbarkeitsgruppe.

Die folgende Transact-SQL-Skript verknüpft eine SQL Server-Instanz mit einer verfügbarkeitsgruppe namens `ag1`. Aktualisieren Sie das Skript für Ihre Umgebung. Führen Sie für jede SQL Server-Instanz, die ein sekundäres Replikat hostet die folgende Transact-SQL, um die verfügbarkeitsgruppe zu verknüpfen.

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

>[!IMPORTANT]
>Nachdem Sie die verfügbarkeitsgruppe erstellt haben, müssen Sie die Integration mit einer Cluster-Technologie wie Schrittmacher für hohe Verfügbarkeit konfigurieren. Für eine schreibgeschützte mit horizontaler Skalierung-Konfiguration, die Verwendung von Verfügbarkeitsgruppen, beginnend mit [!INCLUDE [SQL Server-Version](..\includes\sssqlv14-md.md)], das Einrichten eines Clusters ist nicht erforderlich.

Wenn Sie die in diesem Dokument beschriebenen Schritte ausführen, müssen Sie eine verfügbarkeitsgruppe, die noch nicht gruppiert ist. Der nächste Schritt besteht, um den Cluster hinzuzufügen. Diese Konfiguration gilt für read Scale-Out/Load balancing Szenarien, es ist nicht vollständig für hohe Verfügbarkeit. Für hohe Verfügbarkeit müssen Sie als Clusterressource der verfügbarkeitsgruppe hinzuzufügen. Finden Sie unter [nächste Schritte](#next-steps) Anweisungen. 

## <a name="notes"></a>Hinweise

>[!IMPORTANT]
>Nachdem Sie den Cluster konfigurieren und als Clusterressource der verfügbarkeitsgruppe hinzufügen, können nicht Sie Transact-SQL verwenden, um die verfügbarkeitsgruppenressourcen Failover. SQL Server-Cluster-Ressourcen unter Linux werden mit dem Betriebssystem nicht als eng verbunden, da es sich auf einem Windows Server Failover Cluster (WSFC) handelt. SQL Server-Dienst ist nicht über das Vorhandensein des Clusters. Alle Orchestrierung erfolgt über die Verwaltungstools. Verwenden Sie in RHEL oder Ubuntu `pcs`. Verwenden Sie SLES `crm`. 

>[!IMPORTANT]
>Wenn die verfügbarkeitsgruppe eine Clusterressource ist, besteht ein bekanntes Problem in der aktuellen Version, in denen erzwungenes Failover ohne Datenverlust zu einem Replikat im asynchronen nicht funktioniert. Dies wird in der zukünftigen Version behoben werden. Manuelle oder automatische Failover auf ein synchrones Replikat erfolgreich ausgeführt wird. 


## <a name="next-steps"></a>Nächste Schritte

[Konfigurieren Sie Red Hat Enterprise Linux-Cluster für SQL Server-Verfügbarkeitsgruppe Clusterressourcen](sql-server-linux-availability-group-cluster-rhel.md)

[Konfigurieren von SUSE Linux Enterprise Server-Cluster für Clusterressourcen für SQL Server-Verfügbarkeitsgruppe](sql-server-linux-availability-group-cluster-sles.md)

[Konfigurieren Sie Ubuntu-Cluster für SQL Server-Verfügbarkeitsgruppe Clusterressourcen](sql-server-linux-availability-group-cluster-ubuntu.md)
