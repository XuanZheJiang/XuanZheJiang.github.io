---

layout: post
title: NSString与NSDate、NSData互转
description: NSString转NSDate(类方法)......
category: blog

---
###### NSString转NSDate(类方法)
___
    +(NSDate*) convertDateFromString:(NSString*)uiDate{
        NSDateFormatter *formatter = [[NSDateFormatter alloc] init] ;
        [formatter setDateFormat:@"yyyy年MM月dd日"];
        NSDate *date=[formatter dateFromString:uiDate];
        return date;
    }

###### NSString转NSDate(实例方法)
输入的日期字符串形如：@"2016-05-04 13:08:08"  

    - (NSDate *)dateFromString:(NSString *)dateString{
        NSDateFormatter *dateFormatter = [[NSDateFormatter alloc] init];
        [dateFormatter setDateFormat: @"yyyy-MM-dd HH:mm:ss"]; 
        NSDate *destDate= [dateFormatter dateFromString:dateString];
        return destDate;
    }

###### NSDate转NSString(实例方法)
___
    - (NSString *)stringFromDate:(NSDate *)date{
        NSDateFormatter *dateFormatter = [[NSDateFormatteralloc] init]; 
        [dateFormatter setDateFormat:@"yyyy-MM-dd HH:mm:ss zzz"];//zzz表示时区
        NSString *destDateString = [dateFormatter stringFromDate:date];
        return destDateString;
    }

###### NSString转NSData
___
    NSData* xmlData = [@"testdata" dataUsingEncoding:NSUTF8StringEncoding];

###### NSData转NSString 
___
    NSData * data; 
    NSString *result = [[NSString alloc] initWithData:data  encoding:NSUTF8StringEncoding];

###### NSData转char*
___
    NSData *data; 
    char *test=[data bytes];

###### char*转NSData
___
    byte* tempData = malloc(sizeof(byte)*10); 
    NSData *content=[NSData dataWithBytes:tempData length:10];

