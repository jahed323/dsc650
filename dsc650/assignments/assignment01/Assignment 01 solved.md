---
title: Assignment 1
subtitle: Computer performance, reliability, and scalability calculation
author: Jahedur Rahman
---

## 1.2 

#### a. Data Sizes

| Data Item                                  | Size per Item | 
|--------------------------------------------|--------------:|
| 128 character message.                     | 128 Bytes     |
| 1024x768 PNG image                         | 3 MB          |
| 1024x768 RAW image                         | 1.5 MB        | 
| HD (1080p) HEVC Video (15 minutes)         | 160 MB        |
| HD (1080p) Uncompressed Video (15 minutes) | 160,180 MB    |
| 4K UHD HEVC Video (15 minutes)             | 641 MB        |
| 4k UHD Uncompressed Video (15 minutes)     | 640,723 MB    |
| Human Genome (Uncompressed)                | 200 GB        |

Explanations:

128 character message = 128 characters * 8 bits = 1024 bits; 1024 bits / 8 = 128 bytes

1024x768 PNG image = 1024 * 768 = 786,432 pixels; 786,432 * 32 bits = 25,165,824 bits; 25,165,824 / 8 = 3,145,728 bytes; 3,145,728 / 1024 = 3,072 KB / 1024 = 3 MB

1024x768 RAW image = 1024 * 768 = 786,432 pixels; 786,432 * 16 bits = 12,582,912 bits; 12,582,912 / 8 = 1,572,864 bytes; 1,572,864 / 1024 = 1,536 KB / 1024 = 1.5 MB

HD (1080p) HEVC Video (15 minutes) = 1920 * 1080 = 2,073,600; 2,073,600 * 24 bit = 49,766,400; 49,766,400 * 30 fps * 900 seconds = 1,343,692,800,000 bits; 1,343,692,800,000 / 8 = 167,961,600,000 bytes; 167,961,600,000 / 1024 = 164,025,000 KB; 164,025,000 / 1024 = 160,180 MB / 1000 (HEVC compression ratio) = 160 MB

HD (1080p) Uncompressed Video (15 minutes) = 1920 * 1080 = 2,073,600; 2,073,600 * 24 bit = 49,766,400; 49,766,400 * 30 fps * 900 seconds = 1,343,692,800,000 bits; 1,343,692,800,000 / 8 = 167,961,600,000 bytes; 167,961,600,000 / 1024 = 164,025,000 KB; 164,025,000 / 1024 = 160,180 MB

4K UHD HEVC Video (15 minutes) = 3840 * 2160 = 8,294,400; 8,294,400 * 24 bit = 199,065,600; 199,065,600 * 30 fps * 900 duration in seconds = 5,374,771,200,000 bits; 5,374,771,200,000 / 8 = 671,846,400,000 bytes; 671,846,400,000 / 1024 = 656,100,000 KB; 656,100,000 / 1024 = 640,723 MB / 1000 (HEVC compression ratio) = 641 MB

4k UHD Uncompressed Video (15 minutes) = 3840 * 2160 = 8,294,400; 8,294,400 * 24 bit = 199,065,600; 199,065,600 * 30 fps * 900 duration in seconds = 5,374,771,200,000 bits; 5,374,771,200,000 / 8 = 671,846,400,000 bytes; 671,846,400,000 / 1024 = 656,100,000 KB; 656,100,000 / 1024 = 640,723 MB

Human Genome (Uncompressed) = https://medium.com/precision-medicine/how-big-is-the-human-genome-e90caa3409b0

#### b. Scaling

|                                           | Size     | # HD | 
|-------------------------------------------|---------:|-------:|
| Daily Twitter Tweets (Uncompressed)       | 60 TB    | 18     |
| Daily Twitter Tweets (Snappy Compressed)  | 40 TB    | 12     |
| Daily Instagram Photos                    | 215 TB   | 64.5   |
| Daily YouTube Videos                      | 440 TB   | 132    |
| Yearly Twitter Tweets (Uncompressed)      | 21.4 PB  | 6,570  |
| Yearly Twitter Tweets (Snappy Compressed) | 14.3 PB  | 4,380  |
| Yearly Instagram Photos                   | 76.6 PB  | 23,543 |
| Yearly YouTube Videos                     | 156.8 PB | 48,180 |

Explanations:

Daily Twitter Tweets (Uncompressed) = 500,000,000 tweets * 128 Bytes = 64,000,000,000 Bytes; 64,000,000,000 / 1024 = 62,500,000 MB; 62,500,000 / 1024 = 61,035 GB; 61,035 / 1024 = 60 TB; 60 TB * 3 hdfs copies = 180 TB; 180 / 10 TB HDs = 18 HDs

Daily Twitter Tweets (Snappy Compressed) = 500,000,000 tweets * 128 Bytes = 64,000,000,000 Bytes; 64,000,000,000 / 1024 = 62,500,000 MB; 62,500,000 / 1024 = 61,035 GB; 61,035 / 1024 = 60 TB; 60 TB / 1.5 compression ratio = 40 TB; 40 * 3 hdfs copies = 120 TB; 120 / 10 TB HDs = 12 HDs

Daily Instagram Photos = 75,000,000 * 3 MB = 225,000,000 MB; 225,000,000 / 1024 = 219,727 GB; 219,726 / 1024 = 215 TB; 215 * 3 hdfs copies = 645 TB; 645 / 10 TB HDs = 64.5 HDs

Daily YouTube Videos = 500 hours * 60 min = 30,000 hrs/hr; 30,000 * 24 = 720,000 hrs/day; 720,000 * 60 = 43,200,000 min/day; 43,200,000 / 15 min = 2,880,000 videos; 2,880,000 * 160 MB = 460,800,000 MB; 460,800,000 / 1024 = 450,000 GB; 450,000 / 1024 = 440 TB; 440 * 3 hdfs copies = 1,320 TB; 1,320 / 10 TB HDs = 132 HDs

Yearly Twitter Tweets (Uncompressed) = 60 TB * 365 days = 21,900 TB; 21,900 / 1024 = 21.4 PB; 18 * 365 = 6,570 HDs

Yearly Twitter Tweets (Snappy Compressed) = 40 TB * 365 days = 14,600 TB; 14,600 / 1024 = 14.3 PB; 12 * 365 = 4,380 HDs

Yearly Instagram Photos = 215 * 365 = 78,475 TB; 78,475 / 1024 = 76.6 PB; 64.5 * 365 = 23,542.5

Yearly YouTube Videos = 440 * 365 = 160,600 TB; 160,600 / 1024 = 156.8 PB; 132 * 365 = 48,180

#### c. Reliability
|                                    | # HD | # Failures |
|------------------------------------|-----:|-----------:|
| Twitter Tweets (Uncompressed)      | 6,570| 23         |
| Twitter Tweets (Snappy Compressed) | 4,380| 15         |
| Instagram Photos                   |23,543| 83         |
| YouTube Videos                     |48,180| 171        |

Explanations:

Twitter Tweets (Uncompressed) = 763 / 215,011 = .0035; 6,570 * .0035 = 23

Twitter Tweets (Snappy Compressed) = 763 / 215,011 = .0035; 4,380 * .0035 = 15

Instagram Photos = 763 / 215,011 = .0035; 23,543 * .0035 = 83

YouTube Videos = 763 / 215,011 = .0035; 48,180 * .0035 = 171

#### d. Latency

|                           | One Way Latency      |
|---------------------------|---------------------:|
| Los Angeles to Amsterdam  | 143.483 ms           |
| Low Earth Orbit Satellite | 40 ms                |
| Geostationary Satellite   | 600 ms               |
| Earth to the Moon         | 1,300 ms             |
| Earth to Mars             | 3 - 21 minutes       | 

Explanations:

Los Angeles to Amsterdam = https://wondernetwork.com/pings/Los%20Angeles/Amsterdam

Low Earth Orbit Satellite = https://www.omniaccess.com/leo/

Geostationary Satellite = https://www.omniaccess.com/leo/

Earth to the Moon = https://www.spaceacademy.net.au/spacelink/commdly.htm

Earth to Mars = https://www.spaceacademy.net.au/spacelink/commdly.htm