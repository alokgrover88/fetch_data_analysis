data <- readLines("users.json", encoding = "UTF-8") %>% lapply(fromJSON)

# Max Object Length
k = 0
for(i in 1:length(data)){
  c <- length(data[[i]])
  k <- max(c, k)
}

users <- as.data.frame(matrix(0,length(data), 7))

colnames(users) <- c("id_oid", "active", "createdDate", "lastLogin", "role", "signUpSource", "state")

for(i in 1:length(data)){
  
  users$id_oid[i] <- data[[i]]$`_id`$`$oid`
  
  users$active[i] <- data[[i]]$active
  
  val <- data[[i]]$createdDate
  
  users$createdDate[i] <- ifelse(is.null(val), "-", val)
  
  val <- data[[i]]$lastLogin
  
  users$lastLogin[i] <- ifelse(is.null(val), "-", val)
  
  val <- data[[i]]$role
  
  users$role[i] <- ifelse(is.null(val), "-", val)
  
  val <- data[[i]]$signUpSource
  
  users$signUpSource[i] <- ifelse(is.null(val), "-", val)
  
  val <- data[[i]]$state
  
  users$state[i] <- ifelse(is.null(val), "-", val)
  
}

library(lubridate)
#Convert UNIX timestamp
users$createdDate <- as_datetime(as.integer(users$createdDate))

users$lastLogin <- as_datetime(as.integer(users$lastLogin))

users_temp <- users[!duplicated(users), ]

length(unique(users_temp$id_oid))
