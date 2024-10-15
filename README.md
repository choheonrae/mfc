#void CMy7View::OnDraw(CDC* pDC)
{
    CMy7Doc* pDoc = GetDocument();
    ASSERT_VALID(pDoc);
    if (!pDoc)
        return;

    // 클라이언트 영역 크기 가져오기
    CRect r;
    GetClientRect(&r);

    // 임의의 타원 영역 생성
    int left = rand() % r.Width();
    int top = rand() % r.Height();
    int right = left + (rand() % (r.Width() - left)); // 오른쪽 경계
    int bottom = top + (rand() % (r.Height() - top)); // 아래쪽 경계
    CRect rr(left, top, right, bottom);

    // 임의의 색상 선택
    COLORREF rc = RGB(rand() % 256, rand() % 256, rand() % 256);

    // 브러시 생성
    CBrush brush(rc);
    CBrush* pOldBrush = pDC->SelectObject(&brush);

    // 타원 그리기
    pDC->Ellipse(rr); // 타원을 채우기

    // 이전 브러시 복원
    pDC->SelectObject(pOldBrush);
}
