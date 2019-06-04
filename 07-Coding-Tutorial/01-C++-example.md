# C++ example

* for_each 用法

```c++
    std::for_each(matchIdxsInCell.begin(), matchIdxsInCell.end(),
                  [&inlierMatchIdxs](const MatchIdx& matchIdx)
                  {
                    inlierMatchIdxs.push_back(matchIdx);
                  });
```

```c++
    std::vector<cv::Point2f> newKppts;
    newKppts.reserve(kppts.size());
    std::for_each(kppts.begin(), kppts.end(),
                  [&](const cv::Point2f& pt)
                  {
                      newKppts.push_back(recitfyKpPt(pt)); 
                  });
```

* stable_partition 用法
* find 用法

```c++
    int helpIndx(0);
    auto funcInlierCheck = [&](const MatchPoint_t& mp)
                           {
                                return std::find(inInliers.begin(), inInliers.end(), helpIndx++) != inInliers.end();
                           };
    auto bound = std::stable_partition(std::begin(vMatchPoints),
                                       std::end(vMatchPoints),
                                       funcInlierCheck);
    const auto inputSize = vMatchPoints.size();
    vMatchPoints.erase(bound, vMatchPoints.end())
```

* find_if 用法

```c++
    auto iterMatch = std::find_if(inMatches_.begin(), inMatches_.end(),
                                  [&matchElem](const SLAM::Matcher::Match& elem)
                                  {
                                      return elem.nFirst == matchElem.nFirst && elem.nSecond == matchElem.nSecond;
                                  })
```

* sort 用法
* unique 用法

```c++
    std::sort(inlierMatchIdxs.begin(), inlierMatchIdxs.end());
    auto newEnd = std::unique(inlierMatchIdxs.begin(), inlierMatchIdxs.end());
    inlierMatchIdxs.erase(newEnd, inlierMatchIdxs.end())
    inliers.reserve(matchIdxs.size());
    std::for_each(matchIdxs.begin(), matchIdxs.end(),
                  [&inliers](const MatchIdx& i)
                  {
                    inliers.push_back(i);
                  });
```