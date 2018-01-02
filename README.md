# rewrite
ECMALL常见URL的伪静态规则参考

下载ISAPI_RewriteSnapin.dll及Rewrite.dll
--针对IIS服务器---以下保存为httpd.conf文件----

RegistrationName=GERREN for ecmail
RegistrationCode=XXXX-XXXX-XXXX-XXXX

[ISAPI_Rewrite]
# 3600 = 1 hour 
CacheClockRate 3600
RepeatLimit 32
RewriteEngine On

RewriteCond %{HTTP:Host} ^abc.cc
RewriteRule (.*) http://www.abc.cc [NC,R=301]

#商品
RewriteRule ^/goods/(([0-9]+)\.html)$ /index.php?app=goods&id=$1 [NC]
             
#商品评论、销售记录、商品咨询
RewriteRule ^/goods/([^/]+)/(([0-9]+)\.html)$ /index.php\?app=goods&act=$1&id=$2 [NC]
              
#商品评论、销售记录、商品咨询分页
RewriteRule ^/goods/page_([^/]+)/([^/]+)/(([0-9]+)\.html)$ /index\.php\?app=goods&page=$1&act=$2&id=$3 [NC]   
                     
#全部品牌
RewriteRule ^/brand/?$ /index.php\?app=brand [NC]

#商品总分类列表
RewriteRule ^/category/goods/?$ /index.php\?app=category [NC]

#采购
RewriteRule ^/caigous/(([0-9]+)\.html)$ /index.php?app=caigous&id=$1 [NC]
RewriteRule ^/caigous/([^/]+)/(([0-9]+)\.html)$ /index.php\?app=caigous&act=$1&id=$2 [NC]
RewriteRule ^/caigous/page_([^/]+)/([^/]+)/(([0-9]+)\.html)$ /index\.php\?app=caigous&page=$1&act=$2&id=$3 [NC]

#团购
RewriteRule ^/groupbuy/([0-9]+).html$ /index.php?app=groupbuy&id=$1 [NC]
RewriteRule ^/groupbuy/([^/]+)/(([0-9]+)\.html)$ /index.php\?app=groupbuy&act=$1&id=$2 [NC]


#促销
RewriteRule ^/cuxiao/([0-9]+).html$ /index.php?app=cuxiao&id=$1 [NC]
RewriteRule ^/cuxiao/([0-9]+)/([^/]+)/?$ /index.php\?app=cuxiao&id=$1&act=$2 [NC]


#秒杀
RewriteRule ^/seckill/(([0-9]+)\.html)$ /index.php?app=seckill&id=$1 [NC]
RewriteRule ^/seckill/([0-9]+)/([^/]+)/?$ /index.php\?app=seckill&id=$1&act=$2 [NC]
     
                        
#文章分类及分页
RewriteRule ^/article/([0-9]+)/cate_id/?$ /index.php\?app=article&cate_id=$1 [NC]
RewriteRule ^/article/([0-9]+)/cate_id/page_([^/]+)/?$ /index.php\?app=article&cate_id=$1&page=$2 [NC]

#帮助文档详细页
RewriteRule ^/article/(([0-9]+)\.html)$ /index.php?app=article&act=view&article_id=$1 [NC]

#新闻资讯
RewriteRule ^/news/(([0-9]+)\.html)$ /index.php?app=news&id=$1 [NC]

#店铺导航
RewriteRule ^/store/([0-9]+).html$ /index.php?app=store&id=$1 [NC]
RewriteRule ^/store/article/([0-9]+)\.html$ /index.php\?app=store&act=article&id=$1 [NC]

#信用评价
RewriteRule ^/store/credit/([0-9]+).html$ /index.php?app=store&id=$1&act=credit [NC]
RewriteRule ^/store/([0-9]+)/credit/page_([^/]+)/?$ /index.php\?app=store&id=$1&act=credit&page=$2 [NC]   

RewriteRule ^/store/([0-9]+)/credit/([0-9]+)/?$ /index.php\?app=store&id=$1&act=credit&eval=$2 [NC]
RewriteRule ^/store/([0-9]+)/credit/([0-9]+)/page_([^/]+)/?$ /index.php\?app=store&id=$1&act=credit&eval=$2&page=$3 [NC]

RewriteRule ^/store/([0-9]+)/goods/?$ /index.php\?app=store&id=$1&act=search [NC]
RewriteRule ^/store/([0-9]+)/goods/page_([^/]+)/?$ /index.php\?app=store&id=$1&act=search&page=$2 [NC]

RewriteRule ^/store/([0-9]+)/category/([0-9]+)/?$ /index.php\?app=store&id=$1&act=search&cate_id=$2 [NC]
RewriteRule ^/store/([0-9]+)/category/([0-9]+)/page_([^/]+)/?$ /index.php\?app=store&id=$1&act=search&cate_id=$2&page=$3 [NC]

RewriteRule ^/store/caigou/([0-9]+).html$ /index.php?app=store&id=$1&act=caigou [NC]

RewriteRule ^/store/groupbuy/([0-9]+).html$ /index.php?app=store&id=$1&act=groupbuy [NC]
RewriteRule ^/store/([0-9]+)/groupbuy/page_([^/]+)/?$ /index.php\?app=store&id=$1&act=groupbuy&page=$2 [NC]

RewriteRule ^/store/cuxiao/([0-9]+).html$ /index.php?app=store&id=$1&act=cuxiao [NC]
RewriteRule ^/store/([0-9]+)/cuxiao/page_([^/]+)/?$ /index.php\?app=store&id=$1&act=cuxiao&page=$2 [NC]

RewriteRule ^/store/seckill/([0-9]+).html$ /index.php?app=store&id=$1&act=seckill [NC]
RewriteRule ^/store/([0-9]+)/seckill/page_([^/]+)/?$ /index.php\?app=store&id=$1&act=seckill&page=$2 [NC]

RewriteRule ^/store/news/([0-9]+).html$ /index.php?app=store&id=$1&act=news [NC]
RewriteRule ^/store/([0-9]+)/news/page_([^/]+)/?$ /index.php\?app=store&id=$1&act=news&page=$2 [NC]

#商品分类
RewriteRule ^/search/([0-9]+)/category/?$ /index.php?app=search&act=category&cate_id=$1 [NC]
RewriteRule ^/search/([0-9]+)/category/page_([^/]+)/?$ /index.php?app=search&act=category&cate_id=$1&page=$2 [NC]
RewriteRule ^/search/([0-9]+)/category/region_id_([0-9]+)/?$ /index.php\?app=search&act=category&cate_id=$1&region_id=$2 [NC]  
RewriteRule ^/search/([0-9]+)/category/region_id_([0-9]+)/page_([^/]+)/?$ /index.php\?app=search&act=category&cate_id=$1&region_id=$2&page=$3 [NC]   
        
